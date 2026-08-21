<h1>ExpNo 9: Solve Wumpus World Problem using Python demonstrating Inferences from Propositional Logic</h1> 
<h3>Name: JANANI SREE M                      </h3>
<h3>Register Number/Staff Id:  212225220042              </h3>
<H3>Aim:</H3>
<p>
    To solve  Wumpus World Problem using Python demonstrating Inferences from Propositional Logic
</p>
<h1>Problem Description</h1>
<hr>
<h2>Wumpus World</h2>
<hr>
The Wumpus world is a simple world example to illustrate the worth of a knowledge-based agent and to represent knowledge representation.

The figure below shows a Wumpus world containing one pit and one Wumpus. There is an agent in room [1,1]. The goal of the agent is to exit the Wumpus world alive. The agent can exit the Wumpus world by reaching room [4,4]. The wumpus world contains exactly one Wumpus and one pit. There will be a breeze in the rooms adjacent to the pit, and there will be a stench in the rooms adjacent to Wumpus.

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/cd6b68dc-c79f-4dcb-8126-04da90d65912)

<center>Wumpus World Representation</center>
<p>
This is a python program that uses propositional logic sentences to check which rooms are safe. 

It is assumed that there will always be a safe path that the agent can take to exit the Wumpus world. The logical agent can take four actions: Up, Down, Left and Right. These actions help the agent move from one room to an adjacent room. The agent can perceive two things: Breeze and Stench.
</p>

<hr>
<h1>Sample Input and Output:</h1>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8696111a-a4a7-47cb-ba4b-43a4ef88573f)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/4be5bf06-79fa-4fa0-9334-38a33f06060b)
<h2> Program : </h2>

```

wumpus = [
    ["Save", "Breeze", "PIT", "Breeze"],
    ["Smell", "Save", "Breeze", "Save"],
    ["WUMPUS", "GOLD", "PIT", "Breeze"],
    ["Smell", "Save", "Breeze", "PIT"]
]

row = 0
column = 0
arrow = True
player = True
score = 0

while player:

    choice = input(
        "Press u to move up\n"
        "Press d to move down\n"
        "Press l to move left\n"
        "Press r to move right\n"
    ).lower()

    # ---------------- MOVEMENT ----------------

    if choice == "u":
        if row != 0:
            row -= 1
        else:
            print("Move denied!")

    elif choice == "d":
        if row != 3:
            row += 1
        else:
            print("Move denied!")

    elif choice == "l":
        if column != 0:
            column -= 1
        else:
            print("Move denied!")

    elif choice == "r":
        if column != 3:
            column += 1
        else:
            print("Move denied!")

    else:
        print("Invalid choice!")

    print("Current location:", wumpus[row][column], "\n")

    # ---------------- SMELL / ARROW ----------------

    if wumpus[row][column] == "Smell" and arrow:

        arrow_choice = input(
            "Do you want to throw an arrow?\n"
            "Press y to throw\n"
            "Press n to save your arrow\n"
        ).lower()

        if arrow_choice == "y":

            arrow_throw = input(
                "Press u to throw up\n"
                "Press d to throw down\n"
                "Press l to throw left\n"
                "Press r to throw right\n"
            ).lower()

            target_row = row
            target_column = column

            # Find target cell
            if arrow_throw == "u":
                if row > 0:
                    target_row = row - 1
                else:
                    print("Cannot shoot outside the board!")
                    continue

            elif arrow_throw == "d":
                if row < 3:
                    target_row = row + 1
                else:
                    print("Cannot shoot outside the board!")
                    continue

            elif arrow_throw == "l":
                if column > 0:
                    target_column = column - 1
                else:
                    print("Cannot shoot outside the board!")
                    continue

            elif arrow_throw == "r":
                if column < 3:
                    target_column = column + 1
                else:
                    print("Cannot shoot outside the board!")
                    continue

            else:
                print("Invalid arrow direction!")
                continue

            # Check whether Wumpus is there
            if wumpus[target_row][target_column] == "WUMPUS":

                print("Wumpus killed!")
                score += 1000
                print("Score:", score)

                wumpus[target_row][target_column] = "Save"

                # Remove smell after Wumpus is killed
                for i in range(4):
                    for j in range(4):
                        if wumpus[i][j] == "Smell":
                            wumpus[i][j] = "Save"

            else:
                print("Arrow wasted...")
                score -= 10
                print("Score:", score)

            # Arrow can be used only once
            arrow = False

    # ---------------- WUMPUS ----------------

    if wumpus[row][column] == "WUMPUS":
        score -= 1000
        print("\nWumpus here!!")
        print("You Die!")
        print("Your score is:", score)
        break

    # ---------------- GOLD ----------------

    if wumpus[row][column] == "GOLD":
        score += 1000
        print("\nGOLD FOUND!")
        print("You won....")
        print("Your score is:", score)
        break

    # ---------------- PIT ----------------

    if wumpus[row][column] == "PIT":
        score -= 1000
        print("\nAhhhhh!!!!")
        print("You fell in pit.")
        print("Your score is:", score)
        break

```
<hr>

<h2>Output </h2>
<hr>
<img width="1037" height="757" alt="image" src="https://github.com/user-attachments/assets/eeed8c95-57ed-4c5d-849b-d96dd13d6d15" />
<hr>

<h2> RESULT: </h2>

Thus the program to solve Wumpus World Problem using Python demonstrating Inferences from Propositional Logic has been executed succesfully.
