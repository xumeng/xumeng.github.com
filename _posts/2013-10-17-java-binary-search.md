---
layout: post
title: "java二分法查找"
description: ""
category: 算法
tags: [java 算法]
---


  最近遇到一个问题：

  
  须要在20万号段数据中查找对应的地市，并且这个过程是发生在遍历几百万数据中的。也就是说正常情况下须要执行20万*几百万次。


这个时间太久了，且因为号段是长数字，执行起来速度超慢。


后来经过同事提醒用二分法，顿感算法的牛逼之处。
####二分法的原理就是：把有序的数据分为2段，通过比较得到数据在哪段，然后再把这段的数据分为2段，这样就省去了很多不必要的遍历。
下面两个例子就是二分法的示例，一个是递归，一个是循环。


*java二分法循环示例*
{% highlight java%}
package cn.sunzn.dichotomy;

public class DichotomySearch {
   public static void main(String[] args) {
       int[] arr = new int[] { 12, 23, 34, 45, 56, 67, 77, 89, 90 };
       System.out.println(search(arr, 12));
       System.out.println(search(arr, 45));
       System.out.println(search(arr, 67));
       System.out.println(search(arr, 89));
       System.out.println(search(arr, 99));
   }

   public static int search(int[] arr, int key) {
       int start = 0;
       int end = arr.length - 1;
       while (start <= end) {
           int middle = (start + end) / 2;
           if (key < arr[middle]) {
               end = middle - 1;
           } else if (key > arr[middle]) {
               start = middle + 1;
           } else {
               return middle;
           }
       }
       return -1;
   }
}
{% endhighlight %}


*java二分法递归示例*
{% highlight java %}
/**
 * 二分法查找，必须对已经排好序的序列进行查找，假设现在有一个递增序列，取中间位置的数及序号midIndex=(beginIndex+endIndex)/2，
 * 然后将一个序列折成两半，beginIndex~midIndex，midIndex~endIndex,如果目标数T等于S[midIndex]，找到，
 * 否则，如果T<S[midIndex]，则在beginIndex~midIndex中继续查找；如果T>S[midIndex],则在midIndex~endIndex
 * 中继续查找，如此反复进行，直到找到目标数据，
 * 初始对传入参数进行约束及避免无效计算的条件为，T<S[beginIndex]或T>S[endIndex]或beginIndex>endIndex
 * 或beginIndex>S.length-1||endIndex>S.length-1||beginIndex<0||endIndex<0
 *
 */
package junit.test;

public class BinarySearchTest {
    /**
     * 找到返回索引下标，否则返回-1；
     * @return index
     */
 public int binarySearch(int dataset[],int target,int beginIndex,int endIndex){
  //数组校验
  if(dataset==null||dataset.length==0){
	  return -1;
  }
  //beginIndex,endIndex校验
  if(beginIndex>endIndex||beginIndex>dataset.length-1||endIndex>dataset.length-1||beginIndex<0||endIndex<0){
   System.out.println("error arguments!");
   return -1;
  }
  
  //无效参数处理
  if(target<dataset[beginIndex]||target>dataset[endIndex]||beginIndex>endIndex){
   return -1;
  }
  int midIndex=(beginIndex+endIndex)/2;
  
  //System.out.println(midIndex);
  if(target==dataset[midIndex]){
   return midIndex;
  }
  else if(target<dataset[midIndex]){
   return binarySearch(dataset,target,beginIndex,midIndex-1);//注意midIndex-1
  }
  else{
   return binarySearch(dataset,target,midIndex+1,endIndex);//注意midIndex+1
  }
  
 }
 
 /**
  * @param args
  */
 public static void main(String[] args) {
  // TODO Auto-generated method stub
  BinarySearchTest bs=new BinarySearchTest();
  
  int[] data=new int[]{1,3,5,7,9,12};
  
  int index=bs.binarySearch(data,12,0, 5);
  
  System.out.println("The position of the target number in the array is :"+ index);
 }

}



{% endhighlight %}




后记：算法无穷妙，看来得好好学习下算法。