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

# Average of Final Values

# How a Stack Is Used to Evaluate Postfix Notation

One thing about postfix notation that makes it tricky to evaluate is its 

# Lab Process