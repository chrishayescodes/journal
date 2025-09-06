# Why We Might Be Building Web Apps All Wrong (And How 1990s Tech Could Save Us)

*A conversation about escaping framework prison and rediscovering the lost art of composable software*

[**Shut up and show me the code!**](https://github.com/chrishayescodes/cgi-process-pool)

## TL;DR

Modern web frameworks trap us in monolithic architectures where everything must be written in one language and tightly coupled together. But 1990s CGI had it right: simple, independent programs that do one thing well. The performance problems that killed CGI don't exist anymore—we have process pools, containers, and modern infrastructure. We should return to composable architectures where each endpoint can use the optimal technology, testing becomes trivial, and one bug can't crash your entire application.

## The Problem: We're All Living in Framework Prison

I had an interesting realization recently while talking with Claude about web development: **we've built ourselves into a corner**. 

Think about it. When you start a new project today, your first decision isn't "what's the best way to solve this problem?" It's "Rails or Django? React or Vue? Node or Python?" And once you pick, you're stuck. Your authentication system, your database layer, your API design, your deployment strategy—everything becomes tied to that one choice you made on day one.

Want to write one endpoint in Rust because it needs to be blazingly fast? Too bad, everything has to be JavaScript now. Need to integrate a Python machine learning model? Well, you'll have to wrap it in a REST API and deal with all that network overhead. One small bug in your image processing code? Congratulations, your entire application just crashed.

This is what I've started calling **monolith dystopia**—we traded the beautiful modularity we had in the early web for performance, and now we're stuck with these giant, interconnected applications that are impossible to understand, test, or modify.

But what if there was a better way?

## Going Back to the Beginning: What CGI Got Right

During our conversation, Claude and I started exploring an idea: what if the original web architecture—CGI (Common Gateway Interface)—was actually the right approach all along?

For those who weren't around in the 1990s, CGI was beautifully simple. Each endpoint was just a program. Want a search feature? Write a program that reads query parameters and outputs results. Need user authentication? Write another program. The web server would run your program when someone made a request, and that was it.

```bash
# This was literally how the web worked
/cgi-bin/search.cgi?q=cats
/cgi-bin/login.cgi?user=alice&password=secret
/cgi-bin/cart.cgi?action=add&item=123
```

Each endpoint was completely independent. Your search could be written in C for speed, your admin panel in Python for convenience, and your reporting in R for statistical libraries. One program crashing couldn't affect any other program. Testing was as simple as running the program with some input and checking the output.

It was **composable**. It was **fault-tolerant**. It was **polyglot**. It was **simple**.

So why did we abandon it?

## The Performance Problem (That Doesn't Exist Anymore)

The answer is performance. In the 1990s, starting a new process was expensive. Every web request meant:

1. The web server gets a request
2. Fork a new process 
3. Load your program into memory
4. Execute your code
5. Kill the process
6. Send the response

With 1990s hardware, this took several milliseconds per request. Under any real load, your server would spend more time starting and stopping processes than actually doing useful work.

But here's the thing Claude and I realized: **that problem doesn't exist anymore**.

Modern servers can handle thousands of processes. We have containers that start in milliseconds. We have process pools, where you keep programs running and just hand them new requests. We have sidecars that handle all the boring HTTP stuff while your business logic stays simple.

The infrastructure that killed CGI has been solved. We just never went back to the architecture.

## The Sidecar Revelation

This is where our conversation got really interesting. Claude pointed out that modern infrastructure is actually moving *back* toward the CGI model, just with different names.

Look at the "sidecar pattern" that's become popular in microservices:

```
Request → [Sidecar Proxy] → [Your App]
          ↓
     • Authentication
     • Rate limiting  
     • Logging
     • Metrics
     • Load balancing
```

The sidecar handles all the infrastructure concerns, while your application focuses purely on business logic. Sound familiar? It's exactly what CGI was doing—separating the web server concerns from your program logic.

Kubernetes pods with Envoy sidecars, AWS Lambda functions, Cloudflare Workers—they're all implementing the same basic pattern: **simple programs that focus on one thing, with infrastructure handled separately**.

## The Two-Part Architecture of All Software

During our discussion, we stumbled onto what feels like a fundamental insight: **all software really consists of just two things**:

1. **Context**: Who's asking, when, where, with what permissions, under what conditions?
2. **Logic**: What should we do given that context?

Traditional frameworks mix these together. Your Rails controller has to know about HTTP headers, session management, parameter parsing, *and* your business rules. Your Express route has to handle authentication, validation, logging, *and* the actual work.

But what if we separated them completely?

```
Raw HTTP Request → [Context Pipeline] → [Pure Business Logic]
                   ↓
              • Parse parameters
              • Check authentication  
              • Validate permissions
              • Add user context
              • Log request
```

Your business logic becomes a simple program that gets rich context and just has to decide what to do. No HTTP parsing. No session management. No database connection pooling. Just pure logic.

## Process Pools: Having Your Cake and Eating It Too

"But what about performance?" I asked Claude. "Aren't processes still expensive?"

This led us to explore process pools—the idea that you don't start a new process for every request, you keep a pool of warm processes ready to handle work.

Imagine this:

```c
// Keep 5-10 search processes running at all times
ProcessPool search_pool = {
    .min_processes = 5,
    .max_processes = 20,
    .script_path = "./search.cgi"
};

// When a request comes in:
Process* worker = pool_get_available(&search_pool);
send_request(worker, enriched_context);
response = read_response(worker);
pool_return(&search_pool, worker);  // Back to the pool
```

Suddenly you get:
- **No startup cost** (processes are already warm)
- **True isolation** (each request runs in its own memory space)
- **Horizontal scaling** (add more processes = linear capacity increase)
- **Fault tolerance** (one process crash doesn't affect others)
- **Language diversity** (each endpoint can use the optimal technology)

Modern tools like systemd already do sophisticated process management. Docker handles containerization. Kubernetes orchestrates everything. The infrastructure is there—we just need to use it.

## Testing Becomes Trivial

One of the most compelling aspects Claude and I discussed was how much simpler testing becomes with this architecture.

Instead of this:
```javascript
// Mock the database
// Mock the authentication service  
// Mock the external APIs
// Set up test fixtures
// Start the test server
// Make HTTP requests
// Parse responses
// Clean up everything
```

You get this:
```bash
# Test your business logic directly
export USER_ID="123"
export USER_ROLES="admin,user"  
export QUERY="sensitive search"
echo "$QUERY" | ./search.cgi
```

Your tests become about business scenarios, not infrastructure setup. You can test edge cases by setting environment variables. You can reproduce bugs by running the exact same program with the exact same input.

**Testing becomes about logic, not plumbing.**

## The Polyglot Paradise

Claude and I got excited about the implications for technology choices. In the current framework-centric world, if you choose Django, everything has to be Python. If you choose Rails, everything has to be Ruby.

But with composable CGI services:

- Your high-performance search could be written in Rust
- Your machine learning endpoints could use Python with all its libraries
- Your admin tools could be rapid-prototyped in Ruby
- Your financial calculations could use languages with strong decimal support
- Your legacy integrations could even be COBOL if needed

Each endpoint gets to use the best tool for the job. Your search doesn't care what language your user management is written in. Your billing system doesn't need to understand your recommendation engine.

## Why This Matters Now

Several trends make this architecture particularly relevant today:

**Serverless is popular** because people like small, focused functions—but serverless has vendor lock-in and cold start problems.

**Microservices are hard** because of the operational complexity—but the core idea of small, independent services is sound.

**Containers are mature** enough to make process management easy—we can get isolation without the overhead.

**Security is critical** and process boundaries provide real isolation that language-level security can't match.

## The Convergent Evolution

What's fascinating is that the industry seems to be independently discovering these patterns. Whether it's:

- Serverless functions with context injection
- Container sidecars handling cross-cutting concerns  
- Service meshes separating infrastructure from business logic
- Event-driven architectures with simple handlers

Everyone's moving toward the same basic idea: **small programs that do one thing well, composed through standard interfaces**.

We're not trying to go backward to 1990s technology. We're trying to go forward to 1990s *architecture* with 2020s infrastructure.

## The Bottom Line

After our long conversation exploring these ideas, I'm convinced we've been thinking about web development wrong. We optimized for the performance constraints of 1990s hardware and got stuck with the complexity costs of monolithic frameworks.

But modern infrastructure gives us a different set of tradeoffs. We can have the modularity and simplicity of the early web with the performance and reliability of modern systems.

The question isn't whether we *should* build systems this way. The question is: why aren't we already?

Maybe it's time to escape framework prison and rediscover what made the early web so elegant: **simple programs that do one thing well, composed through standard interfaces**.

The infrastructure is ready. The patterns are proven. The only thing missing is recognizing that sometimes the old ways, enhanced with modern tooling, provide the clearest path forward.

---

*This exploration grew out of a fascinating conversation about software architecture and the realization that we might have overcomplicated web development somewhere along the way. Sometimes the best innovations are really rediscoveries.*