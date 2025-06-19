# Circular-Queue-Array
package queue;

public class CircularQueueArray {
    public static class Cqa{
int front=-1;
int rear=-1;
int size=0;
int[] arr=new int[5];
public void add(int val) throws Exception{   // throws Error deta hai
    if(size==arr.length){
        throw new Exception("full");

    }
    else if(size==0){
        front=rear=0;
        arr[0] =val;

    }
    else if(rear<arr.length-1){     // normal bharne ke liye
        arr[++rear]=val;
    }
    else if(rear==arr.length-1){ // aage se bharne ke liye
        rear=0;
        arr[0]=val;

    }
    size++;

}
public int remove()  throws Exception{
    if(size==0){
        throw new Exception("queue empty");
    }
    else {
        int val=arr[front];
        if(front==arr.length-1) front=0;
        else front++;
        size--;
        return val;
    }

}
public int  peek()  throws Exception{
    if(size==0){
        throw new Exception("queue empty");
    }
    else return arr[front];
}
public boolean isEmpty(){
    if(size==0) return true;
    else return false;
}
public void display(){
    if(size==0){
        System.out.println("empty");
        return;
    }
    else if (front<=rear){
        for(int i=front;i<=rear;i++){
            System.out.println(arr[i]+" ");
        }

    }
    else{  // rear hai jo front se chota hai
        for(int i=front;i<arr.length;i++){
            System.out.println(arr[i]+" ");
        }
        for(int i=0;i<rear;i++){
            System.out.println(arr[i]+" ");
        }

    }
    System.out.println();
}
    }
    public static void main(String[] args) throws Exception {
        Cqa q=new Cqa();
        q.display();
        q.add(1);
        q.add(2);
        q.add(3);
        q.add(4);
        q.display();
        q.remove();
        q.display(); // 2 3 4
        q.add(5);
        q.display();
        q.add(6);
        q.display();
        for(int i=0;i<q.arr.length;i++){ // for printing the actual array
            System.out.println(q.arr[i] +" ");
        }



    }
}
