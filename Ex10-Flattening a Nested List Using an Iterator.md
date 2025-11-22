# Flattening a Nested List Using an Iterator
## DATE:21/11/2025
## AIM:
To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).
## Algorithm
1.Traverse each element in the nested list.

2.If the element is an integer, store it in the flat list.

3.If the element is a list, recursively flatten that list.

4.Use an index pointer to iterate through the flattened list.

5.hasNext() checks if the pointer is inside bounds; next() returns the current element and increments the pointer. 

## Program:
```
/*
Program to find Flattening a Nested List Using an Iterator
Developed by: Vinnush Kumar L S
RegisterNumber: 212223230244
import java.util.*;
public class NestedIterator implements Iterator<Integer> {
    private List<Integer> integers = new ArrayList<>();
    private int position = 0;

    public NestedIterator(List<NestedInteger> nestedList) {
        flattenList(nestedList);
    }

    private void flattenList(List<NestedInteger> nestedList) {
        for (NestedInteger ni : nestedList) {
            if (ni.isInteger()) {
                integers.add(ni.getInteger());
            } else {
                flattenList(ni.getList());
            }
        }
    }

    @Override
    public Integer next() {
        if (!hasNext()) throw new NoSuchElementException();
        return integers.get(position++);
    }
    @Override
    public boolean hasNext() {
        return position < integers.size();
    }
    public static List<NestedInteger> parse(String s) {
    Stack<List<NestedInteger>> stack = new Stack<>();
    List<NestedInteger> curr = new ArrayList<>();
    int num = 0;
    boolean hasNum = false;

    for (int i = 0; i < s.length(); i++) {
        char c = s.charAt(i);
        if (c == '[') {
            stack.push(curr);
            curr = new ArrayList<>();
        } else if (c == ']') {
            if (hasNum) {
                curr.add(new SimpleNestedInteger(num));
                hasNum = false;
                num = 0;
            }
            List<NestedInteger> completed = curr;
            curr = stack.pop();
            curr.add(new SimpleNestedInteger(completed));
        } else if (c == ',') {
            if (hasNum) {
                curr.add(new SimpleNestedInteger(num));
                hasNum = false;
                num = 0;
            }
        } else if (Character.isDigit(c)) {
            num = num * 10 + (c - '0');
            hasNum = true;
        }
    }
    return curr;
}


    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
      
        String input = sc.nextLine();

        List<NestedInteger> nestedList = parse(input);

        NestedIterator iterator = new NestedIterator(nestedList);
        List<Integer> output = new ArrayList<>();
        while (iterator.hasNext()) {
            output.add(iterator.next());
        }

        System.out.println(output);
    }
}

interface NestedInteger {
    boolean isInteger();
    Integer getInteger();
    List<NestedInteger> getList();
}

class SimpleNestedInteger implements NestedInteger {
    private Integer value;
    private List<NestedInteger> list;

    public SimpleNestedInteger(Integer value) {
        this.value = value;
        this.list = null;
    }

    public SimpleNestedInteger(List<NestedInteger> list) {
        this.list = list;
        this.value = null;
    }

    @Override
    public boolean isInteger() {
        return value != null;
    }

    @Override
    public Integer getInteger() {
        return value;
    }

    @Override
    public List<NestedInteger> getList() {
        return list;
    }
}

*/
```

## Output:
<img width="692" height="128" alt="image" src="https://github.com/user-attachments/assets/14d77486-a63e-459c-8282-800e1bf906f6" />


## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.
