CFLAGS = -Wall -fpic -coverage -lm

rngs.o: rngs.h rngs.c
	gcc -c rngs.c -g  $(CFLAGS)

dominion.o: dominion.h dominion.c rngs.o
	gcc -c dominion.c -g  $(CFLAGS)

playdom: dominion.o playdom.c
	gcc -o playdom playdom.c -g dominion.o rngs.o $(CFLAGS)

getCard.o: getCard.h getCard.c
	gcc -c getCard.c -g $(CLAGS)

#To run playdom you need to entere: ./playdom <any integer number> like ./playdom 10*/
testDrawCard: testDrawCard.c dominion.o rngs.o
	gcc  -o testDrawCard -g  testDrawCard.c dominion.o rngs.o $(CFLAGS)

badTestDrawCard: badTestDrawCard.c dominion.o rngs.o
	gcc -o badTestDrawCard -g  badTestDrawCard.c dominion.o rngs.o $(CFLAGS)

testBuyCard: testDrawCard.c dominion.o rngs.o
	gcc -o testDrawCard -g  testDrawCard.c dominion.o rngs.o $(CFLAGS)

testAll: dominion.o testSuite.c
	gcc -o testSuite testSuite.c -g  dominion.o rngs.o $(CFLAGS)

interface.o: interface.h interface.c
	gcc -c interface.c -g  $(CFLAGS)

runtests: testDrawCard 
	./testDrawCard &> unittestresult.out
	gcov dominion.c >> unittestresult.out
	cat dominion.c.gcov >> unittestresult.out


player: player.c interface.o
	gcc -o player player.c -g  dominion.o rngs.o interface.o $(CFLAGS)

all: playdom player testDrawCard testBuyCard badTestDrawCard getCard.o unittest1 unittest2 unittest3 unittest4 cardtest1 cardtest2 cardtest3 cardtest4

clean:
	rm -f *.o playdom.exe playdom player player.exe  *.gcov *.gcda *.gcno *.so *.out testDrawCard testDrawCard.exe unittest1 unittest2 unittest3 unittest4 badTestDrawCard cardtest unittestresults.out

cardtest: cardtest4.c dominion.o rngs.o
	gcc -o cardtest -g cardtest4.c dominion.o rngs.o $(CFLAGS)

#unit tests
unittest1: unittest1.c dominion.o rngs.o getCard.o
	gcc -o unittest1 -g unittest1.c dominion.o rngs.o getCard.o $(CFLAGS)

unittest2: unittest2.c dominion.o rngs.o getCard.o
	gcc -o unittest2 -g unittest2.c dominion.o rngs.o getCard.o $(CFLAGS)

unittest3: unittest3.c dominion.o rngs.o getCard.o
	gcc -o unittest3 -g unittest3.c dominion.o rngs.o getCard.o $(CFLAGS)

unittest4: unittest4.c dominion.o rngs.o getCard.o
	gcc -o unittest4 -g unittest4.c dominion.o rngs.o getCard.o $(CFLAGS)
#card tests
cardtest1: cardtest1.c dominion.o rngs.o getCard.o
	gcc -o cardtest1 -g cardtest1.c dominion.o rngs.o getCard.o $(CFLAGS)

cardtest2: cardtest2.c dominion.o rngs.o getCard.o
	gcc -o cardtest2 -g cardtest2.c dominion.o rngs.o getCard.o $(CFLAGS)

cardtest3: cardtest3.c dominion.o rngs.o getCard.o
	gcc -o cardtest3 -g cardtest3.c dominion.o rngs.o getCard.o $(CFLAGS)

cardtest4: cardtest4.c dominion.o rngs.o getCard.o interface.o
	gcc -o cardtest4 -g cardtest4.c dominion.o rngs.o getCard.o interface.o $(CFLAGS)

tests: unittest1 unittest2 unittest3 unittest4 cardtest1 cardtest2 cardtest3 cardtest4

unittestresults.out: clean tests
	./unittest1 &> unittestresults.out
	gcov unittest1.c -b >> unittestresults.out
	./unittest2 >> unittestresults.out
	gcov unittest2.c -b >> unittestresults.out
	./unittest3 >> unittestresults.out
	gcov unittest3.c -b >> unittestresults.out
	./unittest4 >> unittestresults.out
	gcov unittest4.c -b >> unittestresults.out
	./cardtest1 >> unittestresults.out
	gcov cardtest1.c -b >> unittestresults.out
	./cardtest2 >> unittestresults.out
	gcov cardtest2.c -b >> unittestresults.out
	./cardtest3 >> unittestresults.out
	gcov cardtest3.c -b >> unittestresults.out
	./cardtest4 >> unittestresults.out
	gcov cardtest4.c -b >> unittestresults.out
	gcov dominion.c >> unittestresults.out
	cat dominion.c.gcov >> unittestresults.out
