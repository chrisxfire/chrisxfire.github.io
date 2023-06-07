---
title: notes > dotnet > types > reference types > delegates > action func predicate
date: 2022-05-08T17:27:26-0600
draft: true
---
# Built-in Delegates
Built-in types `Action`, `Func`, and `Predicate` are special delegates that can be used without having to define a new delegate.

# Action
An `Action` delegate points to a method that has no return type.
It is used to perform an action using the arguments of the delegate.
class Program {
static void Main(string[] args) {
Action<string> log = new Action<string>(LogInfo); // The delegate.
log.Invoke("Testing 1 2 3");
}

static void LogInfo(string message) { // The method with no return type.
Console.WriteLine(message);
}
}

# Func
A `Func` delegate accesses multiple input types and specifies the return type.
It is used to transform the arguments of a delegate into a different result.
static void Main(string[] args) {
// Func<*input-type, input-type, return-type*>:
Func<int, int, int> addFunc = new Func<int, int, int>(Add);

int result = addFunc(3, 4);
}

static int Add(int a, int b) {
return a + b;
}

## Another Example
static string ReverseString(string s) {
return new string(s.Reverse().ToArray());
}

static void Main(string[] args) {
Func<string, string> rev = ReverseString;

Console.WriteLine(rev("a string"));
}

Another example: Func<string, bool>: For each string variable passed to the method, return a bool value.

# Predicate
A `Predicate` delegate accepts any type of parameter as input and always returns bool.
It is used to determine if the argument satisfies the condition of the delegate.
static void Main(string[] args) {
Predicate<int> IsEven = new Predicate<int>(IsEvenNumber);
…
}
static bool IsEvenNumber(int number) {
return number % 2 == 0;
}
