# Assignment #3 - Feb 17th to Feb 23rd

###### *Solutions for previous assignments can be found here: https://github.com/ponceoscarj/nlp_python_pilot/tree/main*


## Overall Instructions
1. Watch the following videos:
    1. Lecture 4: Decomposition, Abstraction, and Functions. [[Link]](https://ocw.mit.edu/courses/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/resources/lecture-4-decomposition-abstraction-and-functions/)
    2. Lecture 5: Tuples, Lists, Aliasing, Mutability, and Cloning. [[Link]](https://ocw.mit.edu/courses/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/resources/lecture-5-tuples-lists-aliasing-mutability-and-cloning/)

2. In the #classes-questions channel of slack post at least 1 question related to Lecture 4 or Lecture 5. 

3. Next meeting is at 4pm CST on February 23rd, 2024.


## Python assignment

### Rules:
- Do not use classes or external packages (i.e., regex)
- Only "built-in" functions are allowed


### Submission format:
- Organise your coding by question (e.g., Q1.1.)

### 1. **[Mandatory - Prev Topic1]**: 
You have the following two variables:
```python
word1 = 'wood'
word2 = 'food'

#Let's iterate over word1 by using a "for loop"
for char in word1:
    print(char)
```

#### Q1.1. Why can "char" be replaced with other words or letters? Also, write two new versions of the given "for loop" - one where you replace char with a character and one where you replace it with a word.



#### Q1.2. Use the following coding template to count the number of characters that are the same in both words regardless of their position. Your task is to replace the underlines "___" with your coding to make it work.
_Hint: Slide 11 from Lecture 3 can be helpful_

```python
word1 = 'wood'
word2 = 'food'

count_characters_similar = 0

for ___ in ___:
    for ___ in ___:
        if ___ == ___:
            count_characters_similar += 1

print(f'The number of characters that appear in both words are: {count_characters_similar}')

```



### 2. **[Mandatory - Prev Topic2]**: 
The task of speech recognition systems is to recognise acoustic information (i.e., your voice) and transform it into words. For instance, when you talk to Siri (Apple) or Alexa (Amazon), the first step of these devices is to transform your speech into words, analyse the words (understand what you're saying), decide what to say next - more NLP modelling, and finally transform the words into speech. Speech recognition refers to the first part (i.e., transform speech into words).

_The following paragraph was obtained from from [Jurafsky and Martin's Book](https://web.stanford.edu/~jurafsky/slp3/)_

The standard evaluation metric for speech recognition systems is the word error rate (WER). The word error rate is based on how much the word string returned by the
recognizer (or speech recognition machine) differs from a reference transcription (real word or ground truth).


**Your task** will be to generate a new metric called the "Character error rate" (CER). We want a speech recognition system to excell not only at the word level but also at the character level. 

**BUT** first, let's review some concepts. 

- **String manipulation**: slicing is extremely important in NLP. 
```python
word1_recognised = "FOSTER"
print(word1_recognised[0]) # should print "F"
print(word1_recognised[3]) # should print "T"
```
- **Range() and len()**: Using range() and len() built-in functions together is frequently implemented in NLP models. Understanding this concept is a must! 

```python
word1_recognised = "FOSTER"

len_word1 = len(word1_recognised)
print(len_word1) # should print the integer 6

range_word1 = range(len(word1_recognised))
print(range_word1) # should print "range(0, 6)" - it is class called "range" -> you can prove it by doing print(type(range_word1))

# Why is it important to know range(len(word1))?
# For word and character iteration!!
for char_1 in range(len(word1_recognised)):
    print(char_1) #  What do you think the output is? Try it yourself 


# Now, let's combine slicing, range(), and leng()
for char_1 in range(len(word1_recognised)):
    print(word1[char1]) # What do you think the output is? Try it yourself 
```


#### Q2.1 Character error rate (CER) metric generation

To create our new metric, you will use a "for loop" that iterates over each position of the word and counts the number of times the character in a specific position from both words is different (error) or the same (correct). For instance, in the word "mayo" and "mark" have the same ccharacters in the position 0 and 1, but the characters are different in the position 3 and 4. To create our new CER, we first need to learn how to count both errors and similarities which for our "mayo" and "mark" example are: errors=2 and similarities=2. For simplicity, our CER only works for words that have the same length.

You must use the following python template and replace the underlines "___" with your coding.

```python
word1_recognised = "FOSTER"
word2_reference = "ZOSTER"

char_similarity_count = 0
char_difference_count = 0

for i in range(len(word1_recognised)):
    if ___ == ___:
        char_similarity_count += 1
    elif ___ != ___:
        char_difference_count += 1

print(f'The number of errors are ___, and the number of similarities are ___')
```

### 3. **[Mandatory]**: 

#### 3.1. Creating the CER function.
Now that we know how to count positional differences and similarities. We will create a CER function that takes as input a **tuple** of 2 words and generates a **tuple** of 3 words. The instructions are within the following python template. You must use this template and fill the underlines "___" with your coding.

```python
word1_recognised = "FOSTER"
word2_reference = "ZOSTER"

# Create a tuple of two words: word1 and word2
tuple_words = ___

# Make sure it is a tuple
print(type(tuple_words)) # it should print tuple

# Defining a function called CER and describe the Input and Output within the function - I would recommend that you do the question in this order: 1) fill the underscores, 2) understand the function, and 3) fill the description part. 
def CER(any_tuple_of_two_words):
    """
    Input: ___
    Returns ___
    """ 
    # Split a tuple (or unpuck a tuple) of two words into word1 and word2:

    word1, word2 = ___

    # This is the same as Q2.1 - You must understand this step! 
    char_difference_count = 0

    for i in range(len(word1)):
        if ___ != ___:
            char_difference_count += 1

    # To create the Character Error Rate we need to divide the number of errors by the total number of characters. We have the number of errors (char_difference_count), but we need the total number of characters. 
    # Because both words have the same length, you can only get the length of one word and work with it. In real life scenarios, this almost never happens.
    len_word = ___

    # Now define CER. Remember, it is the division of number of errors by the total number of characters
    CER = ___

    # Now the return has to be a tuple with the following values: CER, char_difference_count, len_word
    return ___                 

# Now, let's make sure our function works
my_character_error_rate, number_errors, length_word = CER(tuple_words)

# Now make it look good in a print statement - be creative:
print(f'___')

```




### 4. **[Mandatory]**: 

#### Adapting your CER function for multiple words.

A group of researchers from St. Andrews University (Scotland, UK) are experts in Quechua languages. Their expertise concentrates in [Southern Quechua](https://en.wikipedia.org/wiki/Southern_Quechua) which is mostly spoken in cities such as Cusco (Peru). They have developed an Automatic Speech Recognition (ASR) system that automatically transcribes their conversations in quechua into words. You are working as an NLP researcher for them. They are aware you know nothing about this language and they are asking you to develop a CER evaluation metric to assess the performance of the system. 

They tested the system with five words and you are given the output of such system or transcribed words (i.e, transcribed_words). You are also given the "gold-standard" transcription or ground truth.

#### 4.1. Creating a function to remove correctly transcribed words
The first task is to remove the correctly transcribed words from the list and save it into a new list. You must use this template and fill the underlines "___" with your coding.

```python
# For this task we are assuming that the number of words are the same in both lists and that a "transcribed word" and their corresponding "gold-standard" word are stored in the same position for both lists. 
# E.g., gold_standard[0] corresponds to transcribed_word[0] and so on. 
gold_standard = ['wacra', 'tayta', 'nanay', 'puka', 'ari']
transcribed_words = ['huacra', 'taita', 'nanai', 'puca', 'ari']

def remove_correct_words(gold_standard, transcribed_words):
    """
    Input: ___
    Returns ___
    """
    len_list = len(gold_standard)
    # if you print(len_list), you should get 5
    # you can test it. Usually this is called debugging. Printing is the first step of debugging when you find a mistake
    # uncomment the next line if you would like to try using a print() within your function.
    # print(len_list)
    
    # Define an empty list where you will append the correct words
    list_correct_words = []

    # loop over each position 
    for element in range(len_list):
        # save the word from each iteration from both lists into the following variables
        word1_recognised = ___
        word2_reference = ___

        # Open a conditional statement comparing if both words are the same
        if ___ == ___:
            
            #if they are the same, pop the word from the list based on its position and save it into the following variables
            # You MUST use the "pop()" function and not "remove()" or "del()"
            
            correct_word1 = ___
            correct_word2 = ___

            # Either can be appended because they must be the same
            list_correct_words.append(correct_word1)


    # You should return three lists
    return ___, ___, ___

# Try your function and print your results
list_correct_words, transcribed_words, gold_standard = remove_correct_words(gold_standard, transcribed_words)
print(list_correct_words, transcribed_words, gold_standard)
```
#### 4.2. What is the difference between `pop()`, `del()`, and `remove()`? Explain and give an example for each by using a list of integers. 

#### 4.3. Create a function to calculate CER (character error rate) that takes two lists as input and outputs a list of calculated CER scores. 
You must use the following python template and fill the underlines "___" with your coding.

You must use the gold_standard and transcribed_words lists after the correctly transcribed word has been removed (or the output of Q4.1.). This means the length of both lists should be 4.

```python
def CER_quechua(gold_standard, transcribed_words):
    """
    Input:
    Returns 
    """

    # Define an empty CER_scores_list
    CER_scores_list = ___

    # Get the length of transcribed_words and save it into len_list_words
    len_list_words = ___

    # for loop iteration over each position within a list
    for ___ in ___: 
        # remember we are iterating over each word based on their position
        # First iteration is the first word in the list or position 0 and so on.
        # Save each word from transcribed_words and gold_standard into the following variables
        word1_recognised = ___
        word2_reference = ___
        
        # count to 0, to start counting the number of errors
        char_difference_count = ___

        # open conditional statement. If both words are different, 
        # generate a CER score by word
        if ___ != ___:
            len_word = len(word1_recognised)

            for ___ in ___:
                if ___ != ___:
                    char_difference_count += 1 
            
            CER_by_word = ___ / ___

            # append CER_by_word to CER_list
            ___
    
    # now return CER_scores_list
    return ___

# Test your function and print your results
# You should obtain a list with four float numbers -> [0.2, 0.2, 0.2, 0.25]

```


### 4. **[Optional-Advanced] Translation system**: 
A group of researchers have developed a transformers-based translation model (Latin to German) and it is believed to perform better than https://translate.google.com/. 

You realise that this system makes a simple mistake; it is unable to translate single words from Latin to compound words in German. You know that compound words is very common in the German language (also called [Agglutinative language](https://en.wikipedia.org/wiki/Agglutinative_language)). You will create a function that corrects the output of the system to correct german. 

You will need the following to complete this task:
```python
latin_words = ['precor', 'arbor', 'tempore']
correct_german = ['ich bete', 'ein baum', 'zu der Zeit']

system_output_german = ['ich*bete', 'ein_baum', 'zu!der!Zeit']

list_special_characters = ['*', '_', '!']
```

You need to create a function allows you to input word by word and automatically corrects it. 

Description of your function:
- The function will ask you to input a word by using the following prompt `"Input the incorrectly translated German word: "`
- You will input each word from the "system_output_german" list individually (by either copy/pasting or typing the word).
- You should use at least one "for loop", one "while loop", one `input()` function, and one `.join()` function. 
- You should use the list "list_special_characters" in your function
- Function should run the function forever unless you input "finito". (I would recommend using "`while True`", but feel free to use other conditions for `while`) 
- Your function should output a list with corrected german words similar to the "correct_german" list.
- The output should be sorted in alphabetical order based on the first character of each compound word.  

