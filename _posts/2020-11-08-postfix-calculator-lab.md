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
    #This creates the Stack class
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

One thing about postfix notation that makes it tricky to evaluate is its variance. Although every postfix expression begins with at least two numbers, the distribution of numbers and operations after that is inconsistent. Thus, a stack with a for loop is very helpful for evaluating postfix notation. With a stack, you can arrange and rearrange the elements in each expression in a stack that we can manipulate to evaluate it. By manipulating it with 'push' and 'pop' based on whether the top element in the stack is a number or an operation, you can rearrange the elements to use each operation to combine two numbers. If the top element is an operation, you want to add it to the top of the stack to combine the following two numbers. If the top element is a number, you can pop it so that the following operation acts on the two most recently popped numbers. These manipulations, plus the peek feature, which allows you to view the top element in the stack, help work through each postfix expression to generate a final value.

# Lab Process