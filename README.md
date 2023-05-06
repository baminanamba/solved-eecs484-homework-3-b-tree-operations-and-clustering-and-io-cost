Download Link: https://assignmentchef.com/product/solved-eecs484-homework-3-b-tree-operations-and-clustering-and-io-cost
<br>
<h1>Q1: B+ Tree Operations</h1>

For the questions in this part, assume these rules for B+ tree operations:

<ul>

 <li>Each node must contain between d &lt;= m &lt;= 2d entries (where m is the number of entries) with the exception of the root node</li>

 <li>The left pointer points to values that are strictly less than the key value.</li>

 <li>During redistribution, favor the right node over the left when both are possible redistribution partners</li>

 <li>During the splitting of a node, the left node will have one more value than the right node</li>

 <li>For insertions, favor redistribution over splitting</li>

 <li>For deletions, favor merging over redistribution</li>

 <li>Only redistribute one entry at a time</li>

</ul>

Draw out the resulting B+ tree after EACH of the the following chains of operations is performed on the given B+ tree.

The operations are:

<ol>

 <li>Insert 11*, 13*</li>

 <li>Insert 9*</li>

 <li>Delete 20*</li>

 <li>Insert 5*</li>

 <li>Insert 1*, 2*, 7*, 8*</li>

 <li>Delete 14*, 15*</li>

</ol>

Draw what the tree should look like at the end of EACH chain of operations–you should have 6 B+ tree drawings. Note that you will be continually updating your tree after each set of operations, NOT restarting with the original tree each time.

<h1>Q2. Clustering and IO cost</h1>

Consider a table Sailors, where there is a B+ tree index on attribute Age, and the following query:

SELECT * FROM Sailors ORDER BY Age;

Furthermore, assume that the first level (root) of the B+ tree is kept in memory at all times, and that the B+ tree has the following properties:

The properties of this B+ tree are:

<ul>

 <li>total size of records = 2MB</li>

 <li>size of record = 1KB</li>

 <li>size of page = 4KB</li>

 <li>the tree has an order of 4</li>

 <li>the fill factor is 67%</li>

</ul>

Assume 1MB = 1024KB. Assume only root node is in memory and nothing else is saved in memory. We try to fit all records in the smallest number of pages possible and each node is in it’s own page. Assume alternate 2 (as described in lecture) is used

Answer the following questions:

<ul>

 <li>What is the number of record pages and leaf nodes? What is the height of the B+ tree?</li>

 <li>How many IOs (worst case) will it take to run this query if our index was clustered?</li>

 <li>How many IOs (worst case) will it take to run this query if our index was unclustered?</li>

</ul>

<h1>Q3. Linear Hashing</h1>

Assume we initialize the Linear Hashing index as follows (the hash function used is given below the Linear Hashing index):

3.1) What is the minimum number of data entries that can be inserted, until we have 4 buckets and level is equal to 1?

3.2) Perform the following insertions on the linear hashing index: 33, 54, 11, 26, 42. Assume that we use the same algorithm discussed in the lecture. Draw the index structure after each insertion, and show the next pointer and level at each step.




<h1>Q4. Extendible Hashing</h1>

In Q3, we looked at linear hashing, but what about extensible hashing? Suppose we have an extendible hash index that uses the hash function:

hashvalue = last ​<em>d</em>​ bits of the binary version of the given number

where ​<em>d</em> is the global depth. We will be using a bucket capacity of 2 for this problem. The initial global depth and local depth are 1. Assume that we use the same hashing function as above (except i is now the global depth)

Our index is initially empty. Then the following insertions occur: 39, 16, 26, 49, 18, 13, 41. Draw the index structure after each insertion. Be sure to clearly show the global and local depths and all bucket pointers at every step.

<h1>Q5. Blocked IOs</h1>

Suppose we have a data set consisting of a 1TB (1T=1024G) file that we need to sort. We have 8GB of memory (RAM) to assist in sorting. The page size of the system is 32KB and the buffer block size is 32KB. Assume that replacement sort is used for the initial pass.

Answer the following questions accordingly:

5.1) How many passes do we need on average to sort the dataset, if we only use replacement sort?

5.2) How many I/Os are needed if we take 15 passes to sort the dataset?

5.3) How many passes do we need if we use blocked I/Os?




<h1>Q6. Bulk Loading</h1>

In this question we will compare the IO cost between bulk loading and repeated insertions.

We make the following assumptions:

<ul>

 <li>10,000 records</li>

 <li>A page size of 1024 bytes</li>

 <li>A tree of order 12</li>

 <li>A pointer/value/search key takes 8 bytes</li>

 <li>Leaf nodes hold as many data entries as possible using alternative 2 (as described in lecture).</li>

 <li>Each node takes up exactly one page of memory.</li>

 <li>Our buffer pool can hold exactly as many pages as the height+1 of the fully created B+tree.</li>

 <li>After bulk loading, all inner nodes are half full.</li>

</ul>

Answer the following questions:

<ul>

 <li>Before bulk loading, we need to sort our record pointers. If we use general external merge sort, how many IOs will it take to do the sort?</li>

 <li>Calculate the IO cost to build the B+ tree. Include the cost of “committing” the changes/saving to disk after completion. For simplicity, assume the buffer pool is flushed before this step. Also assume you can control which pages stay in memory.</li>

 <li>Assume that the average number of IOs taken for each repeated insert is half the height of the final tree. Which method (bulk loading or repeated inserts) requires fewer IOs? By how much?</li>

</ul>





