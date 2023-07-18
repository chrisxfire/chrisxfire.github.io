---
title: notes > .net > fundamentals > benchmarking
date: 2022-01-16T00:00:00-06:00
draft: false
weight: 1
---

# Benchmarking
`dotnet add package BenchmarkDotNet`

`Program.cs`
```cs
using BenchmarkDotNet.Running;

public static void Main() {
	BenchmarkRunner.Run<SomeBenchmarks>();
}
```

`SomeBenchmarks.cs`
```cs
using BenchmarkDotNet.Attributes; // [Benchmark]

public class SomeBenchmarks {
	…
	
	public SomeBenchmarks() {
		…
		[Benchmark(Baseline = true)]
		public string SomeTest() {
			…
		}
		
		[Benchmark]
		public string SomeOtherTest() {
			…
		}
	}
}
```
Then:  
`dotnet run --configuration release`
