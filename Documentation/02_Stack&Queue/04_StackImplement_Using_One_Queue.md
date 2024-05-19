# Stack using one queue

stack with 2 queue is very expensive  in terms of space we need to optimize.

## Pseudocode

- pop works as it should, deque from queue
- while pushing ,
  - calculate size(s) of queue Q
  - Add element to queue
  - one by one we pop all previous entry till size s and push back to queue again

```java
Queue<Integer> q = new LinkedList<>();

void push (int x ){
  int s = q.size();
  q.add(x);
  for(int i = 1; i<=s; i++){
    int temp = q.remove();
    q.add(temp)
  }
}

int pop(){
  if(q1.isEmpty()){
    throw StackIsEmpty();
  }
  
  return q.remove;
}

```
