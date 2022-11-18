## learn-python-projects

Click the snake to see the code and explanation about my code
<!-- 
<details><summary>:snake: </summary>
<p>

```python


```
</p>
</details>

*******************************************
-->
<details><summary>:snake: Hangman with translation to another language</summary>
<p>

```python
import sys
import random
from translate import Translator
translator = Translator(to_lang="fr")

#import draw_man

with open("./word_list.txt") as word_file:
    word_list = word_file.read().split()
word_guess = word_list[random.randrange(len(word_list))]
#word_guess = "eat"
translation = translator.translate(word_guess)
word = list(translation)
print("guess this word in France")
print(word_guess)
#print(translation)
list_word =[]
for i in range(len(word)):
    print('_', end = " ")
    list_word.append('_')
#print(list_word)
wrong_list =[]
#count = 0
while True:


    if len(wrong_list) == 5:
        print()o
        print("you are hanged")
        print(f" the word is : {translation}")

        break
        
    elif list_word == word:

        print("***************")
        print("you win !")
        break
    letter = input("\n input a letter:")
    for i in range(len(word)) :

        if letter == word[i]:

            list_word[i] = letter
    if letter not in word:
        wrong_list.append(letter)
        #count +=1
       # draw_man()
    #print(list_word)
    for i in list_word:

        print(i, end=" ")
    print()
   # print(wrong_list)
    print(" wrong  letter")
    for i in wrong_list:
        print(i, end = " ")



```
</p>
</details>


<details><summary>:snake: language detection and translation with Tkinter</summary>
<p>

```python
from tkinter import *
from translate import Translator
from langdetect import detect
from tkinter import ttk, messagebox
from langcodes import *
import googletrans
from googletrans import Translator
import textblob

root = Tk()
root.title('Tri - language Detection!')
#root.geometry("500x350")
root.geometry("880x500")
translator = Translator()
def translate_it():
    translate_text.delete(1.0, END)
    try:
       for key, value in languages.items():
           if (value == original_combo.get()):
               from_language_key = key

       for key, value in languages.items():
           if (value == translated_combo.get()):
               to_language_key = key
       words = textblob.TextBlob(original_text.get(1.0, END))
       words = words.translate(from_lang=from_language_key , to=to_language_key)
       translate_text.insert(1.0, words)
    except Exception as e:
       messagebox.showerror("Translator", e)

def clear():
    original_text.delete(1.0, END)
    translate_text.delete(1.0, END)



languages = googletrans.LANGUAGES


language_list =list(languages.values())
print(language_list)



original_text = Text(root, height=10, width=40)
original_text.grid(row=0, column=0, pady=20, padx=10)

translate_button = Button(root, text="Translate!",font=("Helvetica",24),command=translate_it)
translate_button.grid(row=0, column=1, padx=10)

translate_text = Text(root, height=10, width=40)
translate_text.grid(row=0, column=2, pady=20, padx=10)

original_combo=ttk.Combobox(root, width=20, value=language_list)
original_combo.current(21)
original_combo.grid(row=1, column=0)

translated_combo=ttk.Combobox(root, width=20, value=language_list)
translated_combo.current(21)
translated_combo.grid(row=1, column=2)

clear_button = Button(root, text="Clear", command=clear)
clear_button.grid(row=2, column=1)





def check_lang():
    if original_text.compare("end-1c","==", "1.0"):
        my_label.config(text="hey! You forget thing")
    else:
        code = detect(original_text.get(1.0, END))
        #code =detectlanguage(original_text.get(1.0, END))
        my_label.config(text=f"your language is : {code}")


# my_text = Text(root, height=10, width=50)
# my_text.grid(row=3, column=0, pady=20, padx=10)
my_button = Button(root, text="check Language", command=check_lang)
my_button.grid(row=3, column=1, pady=20, padx=10)

my_label = Label(root, text="")
my_label.grid(row=3, column=2, pady=20, padx=10)




root.mainloop()


# bahasa = detect("dhahar")
# print(bahasa)
#
#
# translator= Translator(to_lang="id")
# translation = translator.translate("Good Morning!")
# print(translation)

```
</p>
</details>


<details><summary>:snake: most 10 frequent words from a text file with decending order</summary>
<p>

```python
f = open ('./science.txt','r') #replace science.txt with a file
unik ={}
for line in f:
    words = line.split()

    for word in words:
        if word not in unik:
            unik[word] = 1
        else:
            unik[word] = unik[word] + 1
sorted_unik = sorted(unik.items(),key=lambda item:item[1], reverse = True)
count = 0
for k in sorted_unik:
    if count < 10:
        print(k)
    count +=1
print(words)


```
</p>
</details>

<details><summary>:snake: socket connection</summary>
<p>

```python
import socket

my_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
ip = socket.gethostbyname('www.amazon.com')
print(ip)
port = 80
my_socket.connect( (ip, port)        )
print(" I connected")

```
</p>
</details>

<details><summary>:snake: socket server</summary>
<p>

```python
import socket
a = dir(socket)
print(a)
s = socket.socket()
print("made socket object")
port = 12345
s.bind(('',port))
print((f"Socket bound to port {port}"))
s.listen()
print("Socket is listening")
connection_count = 1
#Connection is socket object
#address is the IP address
while True:

    connection, address = s.accept()

    print(f"Server got connection frm {address}")
    if connection_count == 10 :
        connection.send(f"You are lucky".encode())
    else:
        connection.send(f"welcome to my server Thank you for connecting you are client number {connection_count}".encode())
    connection_count +=1
    connection.close()


```
</p>
</details>

<details><summary>:snake: socket client </summary>
<p>

```python
import socket
s = socket.socket()
port = 12345
s.connect(('127.0.0.1', port))
incoming_message = s.recv(1024).decode()
print(incoming_message)


```
</p>
</details>

<details><summary>:snake: Webscrape with beautifull soup</summary>
<p>

```python
from bs4 import BeautifulSoup
import requests


url = "https://www.basketball-reference.com/leagues/NBA_2022_totals.html"
result = requests.get(url)
document = bs4.BeautifulSoup(result.text, "html.parser")
rows = document.find_all("tr", "full_table")
players = []
count = 0
for row in rows:
    stats = row.find_all("td")
    player = []
    for stat in stats:
        if stat.attrs('data-stat') == 'player':
            player.append(stat.text)
            count +=1
        elif stat.attrs['data-stat']=='pts':
            player.append(float(stat.text))
    players.append(player)

print()
players.sort(key=lambda l:l[1],reverse=True)
print(player)

```
</p>
</details>


<details><summary>:snake: Random letter</summary>
<p>

```python
import random
import string

text = ""
for letter in string.ascii_lowercase:
    count = random.randrange(30)
    for i in range(count):
        text = text + letter + " "

print(text)

#find the most frequent  letter inside of the variable text.

text = text.split(" ")
letters={}

for i in text:
    if  i not in  letters :
        letters[i] = 1
    else:
        letters[i] = letters[i]+1
print(letters)
sorted_values = sorted(letters.values())
sorted_letters ={}
for i in sorted_letters:
    for k in letters.keys():
        if letters[k] == i:
            sorted_letters[k] = letters[k]
            break

sorted_letters = sorted(letters.items(),key=lambda item:item[1], reverse = True)

#sorted_letters.reversed()
print(sorted_letters)
count =0
#for i in sorted_letters:
for k in sorted_letters:
    if count < 10:
        print(k)
    count +=1
biggest = 0
for i in letters:
    if letters[i] > biggest:
        biggest = letters[i]
        biggest_key = i


print(f"the most frequent letter is {biggest_key}, it has {biggest} letter ")

#sorted_letters = dict(sorted(letters.items(),key=lambda item:item[1]))
#sorted_letters.reverse()
#print(sorted_letters)
# count = 0
# for key in sorted_letters:
#     print(key)
#     count +=1
#     if count == 10:
#         break
# #
# print(letters)
# print(sorted(letters.values(), reverse = True))
# l = len(letters)
# for i in range(l-1):
#     for j in range(i+1,l):
#         if letters[i] > letters[j]:
#             t = letters[i]
#             letters[i][1] = letters[j][1]
#             letters[j]= t
#         sort_letters = dict(letters)
#         print(sort_letters)


```
</p>
</details>


<details><summary>:snake: Rock paper scissors lizard spock</summary>
<p>

```python
import random

options = ['Rock', 'Paper', 'Scissors', 'Lizard', 'Spock']

# winners = {
#     "Rock": ["Scissors", "Lizard"],
#     "Paper": ["Rock", "Spock"],
#     "Scissors": ["Paper", "Lizard"],
#     "Lizard": ["Paper", "Spock"],
#     "Spock": ["Rock", "Scissors"]
#     }


winners = {
    "Rock": {"Scissors": "crushes", "Lizard": "crushes"},
    "Paper": {"Rock": "covers", "Spock": "disproves"},
    "Scissors": {"Paper": "cuts", "Lizard": "decapitates"},
    "Lizard": {"Paper": "eats", "Spock": "poisons"},
    "Spock": {"Rock": "vaporizes", "Scissors": "smashes"}
}

while True:
    user_choice = input("Rock, Paper, Scissors, Lizard, Spock: ")
    computer_choice = random.choice(options)
    print()
    print(f"You choose {user_choice}")
    print(f"Computer chose {computer_choice}")
    print()
    if user_choice == computer_choice:
        print("Tie")
    elif computer_choice in winners[user_choice]:
        print(f"{user_choice} {winners[user_choice][computer_choice]} {computer_choice}")
        print("You Win")
    else:
        print(f"{computer_choice} {winners[computer_choice][user_choice]} {user_choice}")
        print("You Lose")


# SIMPLE ROCK PAPER SCISSORS

# options = ['Rock', 'Paper', 'Scissors']
#
# user_choice = input("Rock, Paper or Scissors: ")
# computer_choice = random.choice(options)
# print()
# print(f"You choose {user_choice}")
# print(f"Computer chose {computer_choice}")
# print()
# if user_choice == computer_choice:
#     print("Tie")
# elif user_choice == "Paper" and computer_choice == "Rock":
#     print("You Win!")
# elif user_choice == "Rock" and computer_choice == "Scissors":
#     print("You Win!")
# elif user_choice == "Scissors" and computer_choice == "Paper":
#     print("You Win!")
# else:
#     print("You Lose")
# print()
# print()
#
# # elif options[options.index(computer_choice)] == options[options.index(user_choice) - 1]:
# #     print("You Win!")

```
</p>
</details>


<details><summary>:snake: Rock paper scissors </summary>
<p>

```python
import random

list = ["rock", "paper","scissor"]
while True:
    my_chose = input(" chose 'rock,paper,scissor or exit to finish: ")
    if my_chose == "exit":
        break
    comp_chose = list[random.randrange(len(list))]
    print(f"computer chose {comp_chose}")
    if my_chose == comp_chose:
        print("Tie")
    elif my_chose == "scissor" and comp_chose == "paper":
        print("You Win !")
    elif my_chose == "rock" and comp_chose == "scissor":
        print("You Win !")
    elif my_chose == "paper" and comp_chose == "rock":
        print("You Win !")
    else:
        print("you lose !")


```
</p>
</details>

<details><summary>:snake: Read , write with pickle</summary>
<p>

```python
import pickle

class Dummy:
	def __init__(self):
		self.x = 10
	def say_hello(self):

		print("Hello!")

'''
d = Dummy()
#d.say_hello()

f = open('saved_object','wb')
pickle.dump(d,f)
f.close()
'''
f = open('saved_object', 'rb')
new_dummy = pickle.load(f)

new_dummy.say_hello()



```
</p>
</details>

<details><summary>:snake: Read, write from json file</summary>
<p>

```python
'''
#wrong way to read the list
some_list = ['A','B','C']
f = open('saved_list','w')
#f.write(some_list)
f.write(str(some_list))

f.close()


f = open('saved_list', 'r')
new_list = f.read()
new_list = list(new_list)
print(new_list)
print(new_list[0])
'''

#write/read  the correct way

import json
some_list = ['A','B','C']
f = open('saved_list', 'w')
json.dump(some_list,f)
f.close()

f = open('saved_list', 'r')
new_list = json.load(f)
print(new_list)
print(new_list[0])



```
</p>
</details>

<details><summary>:snake: Read, write, readline from text file</summary>
<p>

```python
f = open('my_story.txt', 'w')
f.write("Once upon a time \n")
f.write("There lived a boy \n")
f.write("The end !")
f.close()


f =open("my_story.txt", 'a')
f.write("\nor is it?")

f.close()

'''
f =open("my_story.txt", "w")
f.write("oop")
f.close()
'''

f = open('my_story.txt', 'r')
'''
for line in f:

	print(line.strip()) 
'''
'''
a = f.readline()
print(a)

b = f.readline().strip()
print(b)

c = f.readline().strip()
print(c)

d = f.readline().strip()
print(d)
e = f.readline(3)
print(e)
g = f.readline()
print(g)
all = f.read()
print(all)
a = f.readline().strip()
print(a)
f.readline()
print("****")
print(f.read())
#once up the time There is a boy The end! ****

for line in f:
	if "boy" in line:
		break
print(f.read()) 
'''
f.seek(0)
print(f.readline().strip())

```
my_story.txt
```
Once upon a time 
There lived a boy 
The end !
or is it?
```


</p>
</details>



<details><summary>:snake: Blackjack game</summary>
<p>

```python
#this program is for playing games black jack.
import random
class Card:
	
	def  __init__(self, suit, name):
		self.suit = suit
		self.name = name
		if name =="Ace":
			self.value = 11 
		elif name == "King" or name =="Queen" or name =="Jack":
			self.value = 10
		else:
			self.value = int(name)
		
	def get_card(self):
		return f"{self.name} of {self.suit} worth {self.value}"	
class Hand:
	def __init__(self):
		self.cards = []
		self.total = 0 
	#hide card will be boolean, indicating if I want to hide a card.
	def print_cards(self,hide_card=False):
		if hide_card == True:
			print(self.cards[0].get_card())
			print("<**HIDDEN**>")
		else:

			for i in range(len(self.cards)):
				print(self.cards[i].get_card())
	def add_card(self):
		random_number = random.randrange(len(deck))
		self.cards.append(deck[random_number])
		deck.pop(random_number)
		
		self.compute_total()
	
	def compute_total(self):

		self.total = 0
		aces = 0
		for i in range(len(self.cards)):
			self.total += self.cards[i].value
			if self.cards[i].name == "Ace":
				aces = aces + 1
		if self.total> 21 and aces > 0:
			self.total -=10

def suffle():
	suits = ["Heart", "Diamond", "Club", "Spade"]
	names =["2", "3", "4", "5", "6", "7", "8", "9", "10", "Jack", "Queen", "King", "Ace"]

	local_deck = []
	for suit in suits:
		for name in names:
			card = Card(suit, name)
			local_deck.append(card)
	return local_deck
'''
def adjust_money(money, result):
	if result == "win":
		
	money = money_start
	money += bet
	return money
'''
money = 100

# make a deck list of card, 52 cards object
deck = suffle()

# give amount of  cards to each players

while True:
	
	while True:
		print(f" You have ${money}")
		bet = int(input(" enter your bet: "))
		if bet < 0 or bet > money:
			print("invalid bet")
		else:
			break

	player_hand = Hand()
	dealer_hand = Hand()
	
	if len(deck) < 20:
		deck = suffle()

	for i in range(2):

		player_hand.add_card()
		dealer_hand.add_card()

	#display each person's card

	print("cards on player: ")
	player_hand.print_cards()
	print(f"   player total value: {player_hand.total}")
	print()

	print("cards on dealer: ")
	dealer_hand.print_cards(True)
	#print(dealer_hand.cards[0].get_card())

	# print(f"   dealer total value: {dealer_hand.total}")
	print()

	print("************")
	#hit or stand 
		
	while True:
		print()
		option = input(" 1.Hit 2.stand: ")
		if option == "2":
			break
		elif option == "1":
			player_hand.add_card()
			print("card on player now:")
			player_hand.print_cards()
			print(f"   player total value: {player_hand.total}")
			if player_hand.total > 21:
				break
		else:
			pass
	
	#Dealer reveal hidden card 

	#determining player's value card
	print()

	while dealer_hand.total < 17 and player_hand.total <= 21:
		dealer_hand.add_card()
		#dealer_hand.print_cards()

	print("dealer cards: ")
	dealer_hand.print_cards()	

	print()
	#determining who is win

	if player_hand.total > 21:
		print("you busted, dealer :( win!")
		money -= bet
	elif dealer_hand.total > 21:
		print("Player win, dealer busted")
		money += bet
	elif player_hand.total> dealer_hand.total:
		print("Player Wins!")
		money += bet
	elif player_hand.total == dealer_hand.total:
		print("Tie!")
	else:
		print("Dealer Wins :( !")
		money -= bet

	print(f" player: {player_hand.total};money: {money};  dealer : {dealer_hand.total}")
	
	play = input("play again? y or n: ")
	if play.lower() == "n":
		break
	else:
		pass
	

```
</p>
</details>
