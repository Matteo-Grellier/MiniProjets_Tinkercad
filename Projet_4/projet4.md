# Projet 4 : contrôler un moteur​

## :clipboard: Sujet

> Mettez en place une carte Arduino avec de quoi contrôler un servo-moteur.

## :electric_plug: Le schéma

![image4](./image-4.png)

### Explication du schéma

Dans ce projet, nous avons décidé de faire un système simple avec :
- un servo-moteur **L293D**
- un moteur à courant continu

Le servo-moteur est composé de 16 Pin et peut contrôler 2 moteurs différents.

Donc un côté du servo-moteur, suffit à contrôler notre moteur. On va donc se concentrer sur cette partie.

![image4.2](./image-4.3.png)

Voici le détail des branchements (à noter qu'il marche de la même manière sur l'autre côté du L293D) :

- Le branchement *vert* : Il sert à activer les entrées et sortie.
- Les branchements *jaunes* : Ils servent à contrôler l'entrée du courant, par conséquent le sens de rotation du moteur en sortie.
- Les branchements *violets* : Ils sont relié au moteur, c'est la sortie du courant afin de contrôler le sens du moteur.
- Les branchements *noirs* : Ils sont reliés aux pins de **TERRE**.
- Les branchements *rouges* : Ils sont reliés aux pins d'**Alimentation**.



## :computer: Le code

```c++
int motor_pin_1 = 8;
int motor_pin_2 = 7;

int enable_pin = 10;


void setup()
{
  pinMode(motor_pin_1, OUTPUT); //On active le port d'entrée 1 du L293D
  pinMode(motor_pin_2, OUTPUT); //On active le port d'entrée 2 du L293D
  pinMode(enable_pin, OUTPUT); //On active le port d'activation du L293D
  
  digitalWrite(enable_pin, HIGH); //Dès le démarrage, on active le module pour le moteur aux sorties 1 et 2.
}

void loop()
{
    //Tourne d'un sens.
    digitalWrite(motor_pin_1, HIGH);  
    digitalWrite(motor_pin_2, LOW);
    delay(1000); // Wait for 1000 millisecond(s)
    //Tourne du sens opposés.
    digitalWrite(motor_pin_1, LOW);  
    digitalWrite(motor_pin_2, HIGH);
    delay(1000); // Wait for 1000 millisecond(s)
}
```

### Explication du code

Comme on peut le comprendre grâce aux commentaires dans le code. Le programme fait une chose très simple : Il va faire tourner le moteur d'un sens pendant 1 seconde, et de l'autre sens pendant encore 1 seconde (et ainsi de suite).

Le plus important à comprendre c'est que le servo-moteur va nous permettre de contrôler l'entrée et la sortie du courant et par conséquent le sens de rotation du moteur.

Donc quand on lui dit :

```c++
digitalWrite(motor_pin_1, HIGH);  
digitalWrite(motor_pin_2, LOW);
```
On lui demande d'envoyer le courant vers le ***pin 1*** et d'envoyer en sortie au ***pin 2***.


## :question: La question

### Quels sont les différents moteurs proposés par Tinkercad ? A quoi servent-ils ?​

Il y a en sortie, 5 moteurs différents sur Tinkercad :

- Le *moteur vibrateur* : Comme son nom l'indique, c'est un moteur qui va vibrer (par exemple le système de vibration dans les téléphones).

- Le *moteur à courant continu* : C'est un moteur qui va transformer l'énergie électrique en énergie mécanique. Ici le moteur à courant continue tournera dans un sens (ou dans l'autre via un servo-moteur). Le moteur classique n'aura pas la possibilité de choisir la vitesse via un codeur. Par ailleurs, on peut se servir d'un moteur à courant continu pour produire de l'électricité.

- Le *moteur à courant continu avec codeur* : Dans Tinkercad il y en a 2 types. La seule différence entre les 2 c'est le nombre de Tours par minute possible. Un *moteur à courant continu avec codeur* va permettre de changer la vitesse de rotation du moteur (contrairement à un moteur classique).

- Le *moteur à engrenages* : Moteur composé de 2 engrenages (minimums) dont un qui fournit le couple et l'autre qui est fixée à l'arbre de sortie. L'avantage d'un moteur à engrenages c'est d'avoir une meilleure force de traction. Le moteur tourne moins vite mais la multiplication du couple donne une plus grande force au moteur.

[<-- Projet 3](../Projet_2/Projet_3.md) | 4 | [Projet 5 -->](../Projet_5/projet5.md)