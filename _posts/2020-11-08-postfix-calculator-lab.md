---
layout: post
title: Postfix Calculator Lab
subtitle: Analyzing Postfix Expressions in a Data Set
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [Art of Data]
---

# Code
    #We are referencing a csv file, so we need to import csv
    import csv

    #To evaluate postfix notation, we need to use a stack
    #Creates the Stack class
    class Stack:
        #Constructor method in the Stack class
        def __init__(self, stack=[]):
            self.stack = stack
        #Defines pop
        def pop(self):
            p = self.stack[-1]
            del self.stack[-1]
            return p
        #Defines push
        def push(self, i):
            self.stack.append(i)
        #Defines peek
        def peek(self):
            return self.stack[-1]
        #Defines __repr__ so Python turns the class into a String
        def __repr__(self):
            return str(self.stack)

    #Defines average function to take the average of values in a list
    def average(list):
        sum = 0
        for i in range (0, len(list)):
            sum += list[i]
        average = sum/len(list)
        return average

    #Creates an evaluate function for postfix notation
    def evaluate(list):
        #Sets up the stack that is used to evaluate postfix notation
        stack1 = Stack([])
        #For loop for elements in the list
        for i in range(0, len(list)):
            #If the element in the list is an operation
            if ((list[i] != "+") and (list[i] != "-") and (list[i] != "*")):
                #Push the element
                stack1.push(int(list[i]))
            #If the element in the list is a number    
            else:
                #Variables to pop elements
                a = stack1.pop()
                b = stack1.pop()
                #If addition
                if list[i] == "+":
                    #Adds the popped elements
                    c = a + b
                    stack1.push(int(c))
                #If subtraction
                elif list[i] == "-":
                    c = b - a
                    #Subtracts the popped elements
                    stack1.push(int(c))
                #If multiplication
                elif list[i] == "*":
                    #Multiplies the popped elements
                    c = a * b
                    stack1.push(int(c))
        #Return value
        return(int(stack1.peek()))

    #Creates empty list for final values
    average_final = []

    #Opens the csv file
    with open("calculate_me.csv", "r") as f:
        data = csv.reader(f)
        #Goes through the data
        for row in data:
            #Adds final values to average_final
            average_final.append(evaluate(row))
            #Prints each row
            print(row)
            #Prints the final value of each row
            print(evaluate(row))
    #Uses the average function to find the average of all final values
    print(average(average_final))


# Evaluation of Each Postfix Expression

The final value of each postfix expression goes in order as follows:

* 6
* 40
* -162
* -692
* 2
* -19
* 93
* 95
* -11
* 49000
* 38
* 84
* -100
* 115
* 3
* 142
* 791
* 82
* -192
* -4
* 143
* 3060
* 137
* 384
* 11
* 48
* 805
* 11
* -2700
* 190
* -96
* 1715
* 60
* 48
* -25
* -4
* -135
* -77
* 663
* 40
* 10
* -81
* -15
* -311
* 1095
* 1076
* 1260
* -204
* 91
* 416
* -26
* 34
* -19
* -343
* 11
* -110
* 192
* -63
* -2
* 9
* 13
* -33
* -223
* 152
* 75
* 54
* 517
* 2110
* 412
* 10
* -571
* 3432
* 23
* -48
* 1764
* 7
* 240
* -2
* -936
* 9
* 1
* 5
* 414
* 386
* 128
* -115
* 1
* -18
* 0
* -16186
* 1391
* 29
* 233
* 38
* 63
* 1560
* 591
* -36
* 917
* -25

# Average of Final Values

The average of all of my final values is 529.91.

# How a Stack Is Used to Evaluate Postfix Notation

One thing about postfix notation that makes it tricky to evaluate is its variance. Although every postfix expression begins with at least two numbers, the distribution of numbers and operations after that is inconsistent. Thus, a stack with a for loop is very helpful for evaluating postfix notation. With a stack, you can arrange and rearrange the elements in each expression in a stack that we can manipulate to evaluate it. By manipulating it with 'push' and 'pop' based on whether the top element in the stack is a number or an operation, you can rearrange the elements to use each operation to combine two numbers. If the top element is an operation, you can add it to the top of the stack to combine the two numbers that initally came before it. If the top element is a number, you can pop it so that the following operation acts on the two most recently popped numbers. These manipulations, plus the peek function, which allows you to view the top element in the stack, can help you work through each postfix expression to generate a final value.

# Lab Process

    #We are referencing a csv file, so we need to import csv

    #To evaluate postfix notation, we need to use a stack
    #Creates the Stack class
        #Constructor method in the Stack class
        #Defines pop
        #Defines push
        #Defines peek
        #Defines __repr__ so Python turns the class into a String

    #Defines average function to take the average of values in a list

    #Creates an evaluate function for postfix notation
        #Sets up the stack that is used to evaluate postfix notation
        #For loop for elements in the list
            #If the element in the list is an operation
                #Push the element
            #If the element in the list is a number    
                #Variables to pop elements
                #If addition
                    #Adds the popped elements
                #If subtraction
                    #Subtracts the popped elements
                #If multiplication
                    #Multiplies the popped elements
        #Return value

    #Creates empty list for final values

    #Opens the csv file
        #Goes through the data
            #Adds final values to average_final
            #Prints each row
            #Prints the final value of each row
    #Uses the average function to find the average of all final values

Above is the pseudocode that helped to guide me through the lab. Throughout my experience coding, regardless of the language I am working with, I have benefited greatly from using pseudocode to organize my thoughts and ideas. In this lab, I thought to divide my work into four general steps. The first step was to implement the Stack class into my code so I could use it to evaluate postfix expessions. I received assistance in class on refining my Stack class. The second step was to implement the 'average' function into my code, but I was able to do this easily because I had used this in my last lab. The third step was to create the 'evaluate' function, which evaluates any postfix expression using the Stack class; this process is outlined above. The fourth step was to implement the 'evaluate' function into calculate_me.csv, which evaluated the postfix expressions in this data set, and to implement the 'average' function for the final values, which were averaged to generate one final average. Aside from working to create the Stack class in class, I worked on this lab independently. One thing that worked really well in this lab, as previously addressed, is using pseudocode to outline my final code. One thing that did not work as well is using a trial-and-error method to generate the exact code. For instance, when I was creating my evaluating function, I kept revising my code until it worked for each operation. This is not the most reliable method of coding because if I were dealing with thousands of different cases, instead of merely three operations, I would have had to come up with a more generalizable method. Altogether, this lab taught me not only how to work with postfix notation, notation that I likely will encounter again at some point, but also how to use the Stack class to generate a set of results that I could not have generated as efficiently, or maybe even at all, without the Stack class. This experience helped me learn and grow as a data analyst!