# Market Basket Analysis Cheatsheet

|         Ορολογία         |                                                                                                Επεξήγηση                                                                                                 |                τύπος                |
| :----------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------: |
|   Support (Υποστήριξη)   |                                                                        Πόσο συνά εφαρμόζεται ο κανόνας {Χ,Υ} στο σύνολο δεδομένων                                                                        |  <img src="./images/support.png"/>  |
| Confidence (Εμπιστοσύνη) |                                                             Πόσο συχνά εφαρμόζεται ο κανόνας στα αντικείμενα Υ σε συναλλαγές που περιέχουν Χ                                                             | <img src="./images/confidence.png"> |
|           Lift           | Πόσο ισχυρός είναι ο κανόνας. Αν είναι **κοντά στη μονάδα**, τότε είναι αδύναμος **(θόρυβος)**. Αν είναι **πολύ μεγαλύτερο** από τη μονάδα, τότε είναι χρήσιμη πληροφορία. Ισχύει η συμμετρική ιδιότητα. |     <img src="images/lift.png">     |
|        Conviction        |                                                                        Η πιο ασφαλής επιλογή.Σε αντίθεση με το Lift, δεν ισχύει η συμμετρική ιδότητα συνεπώς η αγορά ενός αγαθού Χ μπορεί να τείνει στην αγορά του Υ, αλλά δεν σημαίνει απαραίτητα πως η αγορά του Υ τείνει στην αγορά του Χ.                                                                  | <img src="images/conviction.png"/>  |

 - Όταν ένα Υποσύνολο Α έχει μεγάλο support (εμφανίζεται συχνά), τότε το υποσύνολο Β το οποίο είναι υποσύνολο του Α (ανήκει στο Α), έχει επίσης μεγάλο support. Ισχύει και το **αντίθετο**.


## Αλγόριθμος Apriori

<img src="./images/apriori.png"/>

1. Αναζητούμε τα στοιχεία με το μικρότερη συχνότητα και τα αφαιρούμε.
2. Προχωρούμε ελέγχοντας τη συχνότητα σε ζευγάρια. Αφαιρούμε αυτά με τη μικρότερη.


Τα υποσύνολα που παρουσιάζουν ενδιαφέρον είναι για αυτά που έχουν πλήθος (ύπο)υποσυνόλου για **n** συχνότητα υποσυνόλου και **r** πλήθος αντικειμένων:

<img src="./images/juice.png"> 

Στο παράδειγμα έχουμε  
n=3, r=2  
=> 3! / 2!(3-2)! = ... = 3.  
Ισχύει, παρατηρώντας:  
<img src="./images/juice_highlight.png">


**Περιττοί (Reduntant) Κανόνες**

Ένας περιττός κανόνας L1 έχει μικρότερο confidence από ένα υποσύνολο του L2. Συγκεκριμένα, για να θεωρηθεί ένας κανόνας L1 περιττός θα πρέπει:

1. conf(L1)<=conf(L2)
2. L2 υποσύνολο του L1