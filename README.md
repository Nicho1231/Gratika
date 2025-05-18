# Gratika
int i = 1, j = 10;
do {
  if (i++ > --j){
    continue;
  }
} while(i < 5);
System.out.println("i = " + i + " and j = " + j);

Iterasi 1: i=1, j=9 → i++ (i=2), 1 > 9 → false

Iterasi 2: i=2, j=8 → i++ (i=3), 2 > 8 → false

Iterasi 3: i=3, j=7 → i++ (i=4), 3 > 7 → false

Iterasi 4: i=4, j=6 → i++ (i=5), 4 > 6 → false

Iterasi 5: loop berhenti (karena i=5 tidak < 5)

Jawaban: B. i = 5 and j = 6
