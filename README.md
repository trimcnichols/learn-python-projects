# learn-python-projects

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
