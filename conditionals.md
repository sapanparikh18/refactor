### DECOMPOSE CONDITIONAL
Method length and nesting are not the only things that contribute to higher cognitive complexity. Conditionals too can make your programs harder to read/debug. For example 
```java
if(date != null && (date.after(today) || !date.after(oneMonthFromToday))){
	//…
}else{
	//…
}
```
The above statement alone has cognitive complexity of 3, which means that it’s 3 times harder to read than the following line.
```java
if(isValidDate(date)){
//	extract method
}else{
// extract method
}
```
Consolidate 
