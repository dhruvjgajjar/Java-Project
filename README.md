A programming language based on java.

What is Scanner? 
Scanner is a class in java.util package used for obtaining the input of the primitive types like int, double, etc. and strings. It is the easiest way to read input in a Java program, though not very efficient if you want an input method for scenarios where time is a constraint like in competitive programming.

Used two classes--
Following Java program comprises of two classes: bank and bank1 respectively , Both classes have their constructors and a method. In the main method, we create objects of two classes and call their methods.
And in this Java program, we will learn how to create a Banking system using Java
In this program, we are using some of the banking related options like Deposit, Withdrawal etc.

More options will be added to this program later ..
STAY TUNED !!
-----------------------------------------------------

FCFS.java
import java.util.Scanner;
public class FCFS {
 public static void main(String[] args) 
 {
 double avwt=0.0,avtat=0.0; 
 int i,j,n, BT[], WT[], TAT[];
 BT = new int[20];
 WT = new int[20];
 TAT = new int[20];
 Scanner sc=new Scanner(System.in);
 System.out.println("Enter number of processes(MAXIMUM 20): ");
 n=sc.nextInt();
 System.out.println("Enter process burst time: ");
 for(i=0;i<n;i++)
 {
 System.out.print("P["+(i+1)+"]: ");
 BT[i]=sc.nextInt();
 }
 WT[0]=0;
 for(i=1;i<n;i++)
 {
 WT[i]=0;
 for(j=0;j<i;j++)
 {
 WT[i]+=BT[j];
 }
 }
 System.out.println("Process\t\tBursttime\t\tWaitingtime\t\tTAT time");
 for(i=0;i<n;i++)
 {
 TAT[i]=BT[i]+WT[i];
 avwt+=WT[i];
 avtat+=TAT[i];
 System.out.println((i+1) + "\t\t\t" + BT[i] + "\t\t\t" + WT[i] + "\t\t\t" + TAT[i]);
 }
 avwt/=i;
 avtat/=i;
 System.out.println("Average Wait Time: "+avwt);
System.out.println("Average Turn Around Time: "+avtat);
 
 }
 
}
--------------------------------+---------------------------------------------+++--------
Fibonacci.java
import java.util.Scanner;
public class Fibonacci extends Thread
{
 public void run()
 {
 try{
 int a=0,b=1,c=0;
 Scanner sc=new Scanner(System.in);
 System.out.println("Enter a limit for series...");
 int n=sc.nextInt();
 System.out.println("Fibonacci series is: ");
 while(n>0)
 {
 System.out.println(c+"");
 a=b;
 b=c;
 c=a+b;
 n=n-1;
 
 }
 
 }
 catch(Exception ex)
 {
 ex.printStackTrace();
 }
 }
 public static void main(String[] args) {
 try
 {
 Fibonacci f=new Fibonacci();
 f.start();
 f.sleep(1000);
 }
 catch(Exception ex)
 {
 ex.printStackTrace();
}
 }
 
}
------------------------------------------------
FIFO_new.java
import java.util.*;
public class FIFO_new {
 public static void main(String[] args)
 {
 Scanner sc=new Scanner(System.in);
 int frames, pointer = 0, hit = 0, fault = 0,ref_len;
 int buffer[];
 int reference[];
 int mem_layout[][];
 System.out.print("Please enter the number of Frames: ");
 frames = sc.nextInt();
 System.out.print("Please enter the length of the Reference string: ");
 ref_len = sc.nextInt();
 reference = new int[ref_len];
 mem_layout = new int[ref_len][frames];
 buffer = new int[frames];
 for(int j = 0; j < frames; j++)
 {
 buffer[j] = -1;
 }
 System.out.println("Please enter the reference string: ");
 for(int i = 0; i < ref_len; i++)
 {
 reference[i] = sc.nextInt();
 }
 System.out.println();
 for(int i = 0; i < ref_len; i++)
 {
 int search = -1;
 for(int j = 0; j < frames; j++)
 {
 if(buffer[j] == reference[i])
 {
 search = j;
 hit++;
 break;
 } 
 }
 if(search == -1)
{
 buffer[pointer] = reference[i];
 fault++;
 pointer++;
 if(pointer == frames)
 {
 pointer = 0;
 }
 }
 for(int j = 0; j < frames; j++)
 {
 mem_layout[i][j] = buffer[j];
 }
 }
 
 for(int i = 0; i < frames; i++)
 {
 for(int j = 0; j < ref_len; j++)
 {
 System.out.printf("%3d ",mem_layout[j][i]);
 }
 System.out.println();
 }
 System.out.println("The number of fault frames: "+hit);
 System.out.println("The number of fault pages: "+(ref_len-hit));
 System.out.println("Fault rate : "+(float) ((float)fault/ref_len));
 } }
---_-------------------------------------------------------------------
FIFO_PageReplacement.java
import java.util.Scanner;
public class FIFO_PageReplacement {
 public static void main(String[] args) 
 {
 Scanner sc =new Scanner(System.in);
 int page_faults=0,m,n,s,pages,frames;
 
 System.out.print("Enter total number of pages: ");
 pages=sc.nextInt();
 int reference_string[]=new int[pages];
 
 System.out.println("Enter values of reference string");
 for(m=0;m<pages;m++)
 {
 reference_string[m]=sc.nextInt();
 }
 System.out.print("Enter total number of frames: ");
 frames=sc.nextInt();
 int temp[]=new int[frames];
 for(m=0;m<frames;m++)
 {
 temp[m]=-1;
 }
 for(m=0;m<pages;m++)
 {
 s=0;
 for(n=0;n<frames;n++)
 {
 if(reference_string[m]==temp[n])
 {
 s++;
 page_faults--;
 }
 }
 page_faults++;
 if((page_faults<=frames)&&(s==0))
 {
 temp[m]=reference_string[m];
}
 else
 {
 temp[(page_faults-1)%frames]=reference_string[m];
 }
 for(n=0;n<frames;n++)
 {
 System.out.print(temp[n]+"\t");
 }
 System.out.println();
 }
 System.out.println("Total page faults: "+page_faults);
 } 
}
------------------LRU.java
import java.util.*;
class LRU
{
 int[] frame,page,present;
 int size,pages,pf=0,flag=0,flag1=0;
 int n,p;
 double faultRate;
 void get()
 {
 Scanner s=new Scanner(System.in);
 System.out.print("Enter frame size:");
 n=s.nextInt();
 System.out.print("Enter no of pages:");
 p=s.nextInt();
 size=n;
 pages=p;
 frame=new int[n];
 present=new int[n];
 page=new int[p];
 System.out.println("Enter pages");
 for(int i=0;i<pages;i++)
 page[i]=s.nextInt();
 for(int i=0;i<size;i++)
 frame[i]=-1;
 }
 int check(int x)
 {
 flag=-1;
 for(int i=0;i<size;i++)
 if(frame[i]==x)
 {
 flag=i;
 break;
 }
 return flag;
 }
 int replace(int x)
 {
 int i;

for(i=0;i<size;i++)
 present[i]=0;
 flag1=0;
 for(i=x-1;i>=0;i--)
 {
 if(check(page[i])>=0)
 {
 flag1++;
 present[check(page[i])]=1;
 }
 if(flag1==(size-1)) 
 break;
 }
 for(i=0;i<size;i++)
 if(present[i]==0)
 {
 flag1=i;
 break;
 }
 return i;
 }
 void lru()
 {
 for(int i=0;i<pages;i++)
 {
 if(i<size)
 {
 frame[i]=page[i];
 pf++;
 for(int j=0;j<size;j++)
 System.out.print(frame[j]+" ");
 System.out.println();
 }
 else
 {
 if(check(page[i])==-1)
 {
 int r=replace(i);
 frame[r]=page[i];
 pf++;
 for(int j=0;j<size;j++)
System.out.print(frame[j]+" ");
 System.out.println();
 }
 else
 {
 for(int j=0;j<size;j++)
 System.out.print(frame[j]+" ");
 System.out.println();
 }
 }
 }
 faultRate=pf/p;
 System.out.println("PAGE FAULT: "+pf);
 System.out.println("Length of string: "+p);
 System.out.println("FAULT RATE: "+faultRate);
 }
 public static void main(String arg[])
 {
 LRU obj=new LRU();
 obj.get();
 obj.lru();
 }
}
----------------------------------------------------
Prime.java
import java.util.*;
public class Prime extends Thread
{
 public void run()
 {
 int n,flag=0,i,j;
 Scanner sc=new Scanner(System.in);
 System.out.println("Enter limit: ");
 n=sc.nextInt();
 System.out.println("Prime Numbers are: ");
 
 for(i=0;i<=n;i++)
 {
 for(j=2;j<i;j++)
 {
 if(i%j==0)
 {
 flag=0;
 break;
 }
 else
 {
 flag=1;
 }
 }
 if(flag==1)
 {
 System.out.println(i);
 }
 }
 }
 public static void main(String[] args) {
 Prime pm=new Prime();
 pm.start();
 } 
}
-----------------Producer_Consumer.java
import java.util.Scanner;
public class Producer_Consumer 
{
 static int mutex=1,full=0,empty=3,x=0;
 static public void producer1()
 {
 mutex=wait(mutex);
 full=signal(full);
 empty=wait(empty);
 x++;
 System.out.println("Producer produces the item: "+x);
 mutex=signal(mutex);
 }
 static public void consumer1()
 {
 mutex=wait(mutex);
 full=wait(full);
 empty=signal(empty);
 System.out.println("Consumer consumes: "+x);
 x--;
 mutex=signal(mutex);
 }
 static public int wait(int s)
 {
 return(--s);
 }
 static public int signal(int s)
 {
 return(++s);
 }
 public static void main(String[] args) {
 System.out.println("Thankyou Saransh!!!");
 int n;
 System.out.println("1.Producer\n2.Consumer\n3.exit");
 while(true)
 {
 Scanner sc=new Scanner(System.in);

System.out.print("Enter your choice: ");
 n=sc.nextInt();
 switch(n)
 {
 case 1: 
 if((mutex==1)&&(empty!=0))
 producer1();
 else
 System.out.println("Buffer is full!!!");
 break;
 
 case 2: 
 if((mutex==1)&&(full!=0))
 consumer1();
 else
 System.out.println("Buffer is empty!!!");
 break;
 
 case 3: 
 return;
 }
 }
 }
}
----------------------------------------------
RoundRobin.java
import java.util.Scanner;
public class RoundRobin 
{
 public static void main(String[] args) 
 { 
 Scanner sc=new Scanner(System.in);
 int count,j,n,time,remain,flag=0,time_quantam=0;
 int wait_time=0,tat=0;
 int at[]=new int[10];
 int bt[]=new int[10]; 
 int rt[]=new int[10]; 
 System.out.print("Enter total process: ");
 n=sc.nextInt();
 remain=n;
 for(count=0;count<n;count++)
 {
 System.out.print("ENTER ARRIVAL TIME AND BURST TIME of process 
"+(count+1)+ ":");
 at[count]=sc.nextInt();
 bt[count]=sc.nextInt();
 rt[count]=bt[count];
 }
 System.out.print("Enter time quantam: ");
 time_quantam=sc.nextInt();
 System.out.println("process\t\tTAT\t\tWaiting time");
 for(time=0,count=0;remain!=0;)
 {
 if(rt[count]<=time_quantam && rt[count]>0)
 {
 time+=rt[count];
 rt[count]=0;
 flag=1;
 }
 else if(rt[count]>0)
 {
 rt[count]-=time_quantam;
 time+=time_quantam;
 }
 if(rt[count]==0 && flag==1)
 {
 remain--;
 int a,b;
 System.out.println("P["+(count+1)+"]\t\t"+(time-at[count])+"\t\t"+(time￾at[count]-bt[count]));
 wait_time+=time-at[count]-bt[count];
 tat+=time-at[count];
 flag=0;
 }
 if(count==n-1)
 {
 count=0;
 }
 else if(at[count+1]<=time)
 {
 count++;
 }
 else
 {
 count=0;
 }
 
 }
 System.out.println("Average Wait_time: "+wait_time*1.0/n);
 System.out.println("Average TAT: "+tat*1.0/n);
 }
}
---------------SJF_Algorithm.java
import java.util.Scanner;
public class SJF_Algorithm {
 public static void main(String[] args) 
 {
 Scanner sc=new Scanner(System.in);
 int i,n,min,k=1,btime=0,temp,j,ta=0,sum=0;
 int p[]= new int [] {1,2,3,4,5,6,7,8,9,10};
 int bt[]=new int[10];
 int at[]=new int[10];
 int wt[]=new int[10];
 int tt[]=new int[10];
 float wavg=0,tavg=0,tsum=0,wsum=0;
 System.out.print("Enter number of processes: ");
 n=sc.nextInt();
 System.out.println("Enter burst time of all processes: ");
 for(i=0;i<n;i++)
 {
 bt[i]=sc.nextInt();
 }
 System.out.println("Enter arrival time of all processes: ");
 for(i=0;i<n;i++)
 {
 at[i]=sc.nextInt();
 }
 for(i=0;i<n;i++)
 {
 for(j=0;j<n;j++)
 {
 if(at[i]<at[j])
 {
 temp=p[j];
 p[j]=p[i];
 p[i]=temp;
 temp=at[j];
 at[j]=at[i];
 at[i]=temp;
 temp=bt[j];
bt[j]=bt[i];
 bt[i]=temp;
 }
 }
 }
 
 for(j=0;j<n;j++)
 {
 btime=btime+bt[j];
 min=bt[k];
 for(i=k;i<n;i++)
 {
 if(btime>=at[i] && bt[i]<min)
 {
 temp=p[k];
 p[k]=p[i];
 p[i]=temp;
 temp=at[k];
 at[k]=at[i];
 at[i]=temp;
 temp=bt[k];
 bt[k]=bt[i];
 bt[i]=temp;
 }
 }
 k++;
 }
 wt[0]=0;
 for(i=1;i<n;i++)
 {
 sum=sum+bt[i-1];
 wt[i]=sum-at[i];
 wsum+=wt[i];
 }
 wavg=(wsum/n);
 for(i=0;i<n;i++)
 {
 ta=ta+bt[i];
 tt[i]=ta-at[i];
 tsum=tsum+tt[i];
 }
 tavg=(tsum/n);
 System.out.println("Process\tburst\tarrival\twaiting\tturnaround");
 for(i=0;i<n;i++)
 {
 System.out.println(p[i]+"\t"+bt[i]+"\t"+at[i]+"\t"+wt[i]+"\t"+tt[i]);
 }
 System.out.println("Average Wait time: "+wavg);
 System.out.println("Average turn around time: "+tavg);
 }
}


