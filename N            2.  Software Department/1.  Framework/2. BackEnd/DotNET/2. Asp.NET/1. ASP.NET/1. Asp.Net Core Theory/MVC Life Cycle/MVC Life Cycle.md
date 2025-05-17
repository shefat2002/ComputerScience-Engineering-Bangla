Step 1: Client sends request ➡️ GET /home/index
Step 2: Kestrel server receives request
Step 3: Middleware pipeline starts
Step 4: Routing identifies controller/action
Step 5: Controller action is prepared
🔁 Step 6: [Action Filters run here]
   ├── OnActionExecutionAsync() (Async wrapper)
   │     ├── OnActionExecuting()      🔹 [BEFORE the action method runs]
   │     └── OnActionExecuted()       🔹 [AFTER the action method runs]
Step 7: Action method runs (e.g. return View())
Step 8: Framework executes ViewResult (ExecuteResultAsync)
Step 9: View engine renders .cshtml
Step 10: HTML is returned to client
