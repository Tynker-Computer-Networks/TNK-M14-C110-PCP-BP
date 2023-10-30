Chat with Multiple Clients
===================


In this activity, you will learn to use multi threading to connect multiple clients to the server and send and receive messages.

<img src= "https://s3.amazonaws.com/media-p.slid.es/uploads/1525749/images/10858944/C110_PCP.gif" width = "521" height = "281" >


Follow the given steps to complete this activity:

* Open the file `client.py`.

* Comment the pass in the get_random_question_answer() function.
~~~python
#pass
~~~

* Move the following code from the while loop to get_random_question_answer function to select the random question 
~~~python
random_index = random.randint(0,len(questions) - 1)
random_question = questions[random_index]
conn.send(random_question.encode('utf-8'))
~~~

* Retrieve the answer corresponding to the same random index from answers list and store it in the random_answer variable.
~~~python
random_answer = answers[random_index]
~~~


* Return a tuple containing three values: the random_index, the random_question, and the random_answer.
~~~python
return random_index, random_question, random_answer
~~~




* Remove the question by calling the remove_question(index) method in the else part of the clientThread() function if the answer current question is incorrect.
~~~python
remove_question(index)
~~~


* Get a new question using the get_random_question_answer(conn) method and update the index, question, and answer variables.
~~~python
index, question, answer = get_random_question_answer(conn)
~~~


* Create a new_Thread in the while loop to target the clientThread function and send conn as an argument. Then start the thread by invoking the start() method on the new_Thread object
~~~python
new_thread = Thread(target= clientThread,args=(conn,addr))
new_thread.start()
~~~


* Save and run the code to check the output.
