---
title: notes > .net > programming models > asynchronous programming > concepts
date: 2022-02-16T00:00:00-06:00
draft: false
weight: 1
---

# Asynchronous vs. Synchronous
Asynchronous code like `FryEggsAsync(2)` does not block:
```cs
static async Task Main() { // the async modifier signals that the method contains an await
	Egg eggs = await FryEggsAsync(2);
	Console.WriteLine("eggs are ready");
}
```

Synchronous code will block the thread executing it from doing any other work.  It cannot be interrupted:
```cs
static void Main() {
	Egg eggs = FryEggs(2);
	Console.WriteLine("eggs are ready");
}
```

# Concurrent
Concurrent code like `Task<Egg> eggsTask = FryEggsAsync(2)` does not block and allows for concurrent execution:
```cs
static async Task Main() {
	Task<Egg> eggsTask = FryEggsAsync(2);
	Eggs eggs = await eggsTask;
	Console.WriteLine("eggs are ready");
}
```

# Composition
If any portion of an operation is asynchronous, the entire operation is asynchronous.  
Composition combines an asynchronous operation with a synchronous operation:
```cs
static async Task<Toast> MakeToastWithButterAndJamAsync() {
	var toast = await ToastBreadAsync();	// the asynchronous operation
	ApplyButter(toast);				// the synchronous operations
	ApplyJam(toast);
	
	return toast;
}
```
