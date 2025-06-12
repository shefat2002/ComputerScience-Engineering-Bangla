
## 💡 C#/.NET LINQ Tip — `First()` vs `FirstOrDefault()` 🚀[Source](https://www.linkedin.com/posts/serkutyildirim_csharp-dotnet-programming-activity-7317533884257128450-6Xzz/?utm_source=social_share_send&utm_medium=android_app&rcm=ACoAAFJCXfcBIcZmlLG5hIrKQjJ7iQQ2Sm6gFI4&utm_campaign=whatsapp)

### 🔍 **What’s the Difference?**

#### ⚡ `First()`

- Use when **you’re sure** the sequence has at least **one element**.
    
- Throws an **exception** if the sequence is **empty**.
    
- Best when an empty sequence is **unexpected** and should signal a problem.
    

#### ⚡ `FirstOrDefault()`

- Use when an **empty sequence is acceptable**.
    
- Returns the **default value** (e.g., `null` for reference types) if the sequence is empty.
    
- Safer for cases where **no match is a valid scenario**.
    

---
### 🔥 Additional Notes:

- Both methods **search forward** through the collection.
    
- `First()` → Throws `InvalidOperationException` if no elements are found.
    
- `FirstOrDefault()` → Returns default (e.g., `null`, `0`, `false`) instead of throwing.
    

---

### ✅ Summary

| Use Case                    | Method             | Behavior When Empty |
| --------------------------- | ------------------ | ------------------- |
| Expect at least one element | `First()`          | Throws exception    |
| May be empty                | `FirstOrDefault()` | Returns default     |
|                             |                    |                     |
