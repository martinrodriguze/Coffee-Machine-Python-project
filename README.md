# Coffee-Machine-Python-project
# Hyperskill project
class Coffee_Machine:

    def __init__(self,dollars, water, milk, cb, cups, things):
        self.dollars = dollars
        self.water = water
        self.milk = milk
        self.cb = cb
        self.cups = cups
        self.things = things

    def state(self,i,v):
        print("\nThe coffee machine has:")
        for i, v in enumerate([self.water, self.milk, self.cb, self.cups]):
            print(f"{v} of {self.things[i]}")
        print(f"${self.dollars} of {self.things[4]}")

    def buy(self,choice):
        #choice = int(input("What do you want to buy man? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu:"))
        global water, milk, cb, dollars, cups
        if choice == "1":
            if self.water >= 250 and self.cb >= 16 and self.cups >= 1:
                self.water = self.water - 250
                self.cb = self.cb - 16
                self.dollars = self.dollars + 4
                self.cups = self.cups - 1
                print('I have enough resources, making you a coffee!')
            else:
                print('Sorry, not enough water!')
        elif choice == "2":
            if self.water >= 350 and self.milk >= 75 and self.cb >= 16 and self.cups >= 1:
                self.water = self.water - 350
                self.milk = self.milk - 75
                self.cb = self.cb - 20
                self.dollars = self.dollars + 7
                self.cups = self.cups - 1
                print('I have enough resources, making you a coffee!')
            else:
                print('Sorry, not enough water!')
        elif choice == "3":
            if self.water >= 200 and self.milk >= 100 and self.cb >= 12 and self.cups >= 1:
                self.water = self.water - 200
                self.milk = self.milk - 100
                self.cb = self.cb - 12
                self.dollars = self.dollars + 6
                self.cups = self.cups - 1
                print('I have enough resources, making you a coffee!')
            else:
                print('Sorry, not enough water!')
        elif choice == 'back':
            control()

    def fill(self,w,m,co,c):
        # global water, milk, cb, cups
        self.water = self.water + w
        self.milk = self.milk + m
        self.cb = self.cb + co
        self.cups = self.cups + c

    def take(self):
        global dollars
        print("I gave you $",self.dollars)
        self.dollars = 0


cm1 = Coffee_Machine(550,400,540,120,9,["water", "milk", "coffee beans", "cups", "money"])
def control():
    action = input("\nWrite action(buy, fill, take, remaining, exit):")
    if action == "buy":
        cm1.buy (input("What do you want to buy man? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu:"))
    elif action == "fill":
        cm1.fill(int(input("Write how many ml of water do you want to add:")),int(input("Write how many ml of milk do you want to add:")),int(input("Write how many g of coffee beans do you want to add:")),int(input("Write how many disposable cups of coffee do you want to add:")) )
    elif action == "take":
        cm1.take()
    elif action == 'remaining':
        cm1.state(0,0)
    elif action == 'exit':
        exit()
    control()

control()
