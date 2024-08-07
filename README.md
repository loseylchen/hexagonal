# hexagonal

import turtle
from math import pi, sin, cos
import random
import time

def draw_hexagon(x, y, side_length, color):
    """Dessine un hexagone centré en (x, y) avec une longueur de côté spécifiée et une couleur"""
    turtle.up()
    turtle.goto(x, y)
    turtle.down()
    turtle.fillcolor(color)
    turtle.begin_fill()
    for _ in range(6):
        angle = turtle.heading()
        turtle.forward(side_length)
        turtle.left(60)
    turtle.end_fill()

def pave(abscisse_centre, ordonnee_centre, longueur_arete, color1, color2, color3):
    """ Dessine avec turtle un pavé hexagonal en position (abscisse_centre, ordonnee_centre)
        paramètres :
        - (abscisse_centre, ordonnee_centre) : point centre du pavé
        - longueur_arete : longueur de chaque arête du pavé
        - color1, color2, color3 : les couleurs des 3 hexagones"""
    # Dessine trois hexagones, déplacés pour former un pavé
    offset = sin(pi / 3) * longueur_arete

    # Premier hexagone (centre)
    draw_hexagon(abscisse_centre, ordonnee_centre, longueur_arete, color1)

    # Deuxième hexagone (au-dessus centre)
    draw_hexagon(abscisse_centre + offset, ordonnee_centre + longueur_arete / 2, longueur_arete, color2)

    # Troisième hexagone (en dessous centre)
    draw_hexagon(abscisse_centre - offset, ordonnee_centre - longueur_arete / 2, longueur_arete, color3)

turtle.hideturtle()
turtle.speed(0)
turtle.reset()

while True:
    pave(random.randint(-300, 300), random.randint(-300, 300),
         random.randint(10, 50), 'black', 'red', 'blue')
    pave(random.randint(-300, 300), random.randint(-300, 300),
         random.randint(10, 50), 'white', 'grey', 'black')
    turtle.update()  # If using turtle.tracer(False) for faster drawing

turtle.done()  # Ensure turtle module completes its drawing
