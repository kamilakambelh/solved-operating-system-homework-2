Download Link: https://assignmentchef.com/product/solved-operating-system-homework-2
<br>
<h1>Part I</h1>

<ol>

 <li>Consider a computer that does not have a TEST AND SET LOCK instruction but does have an instruction to swap the contents of a register and a memory word in a single indivisible action. Can that be used to write a routine <em>enter region </em>such as the one found in Fig. 2–12.</li>

 <li>Measurements of a certain system have shown that the average process runs for a time <em>T </em>before blocking on I/O. A process switch requires a time <em>S</em>, which is effectively wasted (overhead). For roundrobin scheduling with quantum <em>Q</em>, give a formula for the CPU efficiency (i.e., the useful CPU time divided by the total CPU time) for each of the following:

  <ul>

   <li><em>Q</em>=∞</li>

   <li><em>Q&gt;T</em></li>

   <li><em>S&lt;Q&lt;T</em></li>

   <li><em>Q</em>=<em>S</em></li>

   <li><em>Q </em>nearly 0</li>

  </ul></li>

 <li> Consider the interprocess-communication scheme where mailboxes are used. Suppose a process <em>P </em>wants to wait for two messages, one from mailbox <em>A </em>and one from mailbox <em>B</em>. What sequence of send and receive should it execute so that the messages can be received in any order?</li>

 <li>Consider the following program that uses the Pthreads API. What would be the output of the program? (<em>Note that the line numbers are for references only.</em>)</li>

</ol>

Listing 1: pthread.c

<ul>

 <li>#include &lt;stdio.h&gt;</li>

 <li>#include &lt;stdlib.h&gt;</li>

 <li>#include &lt;unistd.h&gt;</li>

 <li>#include &lt;pthread.h&gt;</li>

 <li>#include &lt;sys/types.h&gt;</li>

</ul>

6

7 int value = 1;

8

9 static void *runner(void *param);

10

<ul>

 <li>int main(int argc, char **argv)</li>

 <li>{</li>

 <li>pid_t pid = fork();</li>

 <li>if (pid &gt; 0) {</li>

 <li>printf(“A = %d
”, value);</li>

 <li>}</li>

 <li>else if (pid == 0) {</li>

 <li>pid_t pid = fork();</li>

 <li>if (pid &gt; 0) {</li>

 <li>printf(“B = %d
”, value);</li>

 <li>}</li>

 <li>else if (pid == 0) {</li>

 <li>pid_t pid = fork();</li>

 <li>pthread_t tid;</li>

 <li>pthread_attr_t attr;</li>

 <li>pthread_attr_init(&amp;attr);</li>

 <li>pthread_create(&amp;tid, &amp;attr, runner, NULL);</li>

 <li>pthread_join(tid, NULL);</li>

 <li>if (pid &gt; 0)</li>

 <li>printf(“C = %d
”, value);</li>

 <li>else</li>

 <li>printf(“D = %d
”, value);</li>

 <li>}</li>

 <li>else {</li>

 <li>exit(1);</li>

 <li>}</li>

 <li>}</li>

 <li>else {</li>

 <li>exit(1);</li>

 <li>}</li>

</ul>

41

<ul>

 <li>return 0;</li>

 <li>}</li>

</ul>

44

<ul>

 <li>static void *runner(void *param)</li>

 <li>{</li>

 <li>value += 1;</li>

 <li>pthread_exit(0);</li>

 <li>}</li>

</ul>

<h1>Part II</h1>

Write a program to simulate the dining philosopher problem mentioned in the textbook using the Pthreads API on Linux. Make sure that your implementation is able to handle 5 philosophers and is free of race condition.