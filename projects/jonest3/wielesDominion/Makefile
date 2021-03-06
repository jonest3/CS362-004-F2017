CFLAGS = -Wall -fpic -coverage -lm

rngs.o: rngs.h rngs.c
	gcc -c rngs.c -g $(CFLAGS)

dominion.o: dominion.h dominion.c rngs.o
	gcc -c dominion.c -g $(CFLAGS)

playdom: dominion.o playdom.c
	gcc -o playdom playdom.c -g dominion.o rngs.o $(CFLAGS)
#To run playdom you need to entere: ./playdom <any integer number> like ./playdom 10*/
testDrawCard: testDrawCard.c dominion.o rngs.o
	gcc  -o testDrawCard -g testDrawCard.c dominion.o rngs.o $(CFLAGS)

badTestDrawCard: badTestDrawCard.c dominion.o rngs.o
	gcc -o badTestDrawCard -g badTestDrawCard.c dominion.o rngs.o $(CFLAGS)

testBuyCard: testDrawCard.c dominion.o rngs.o
	gcc -o testDrawCard -g testDrawCard.c dominion.o rngs.o $(CFLAGS)

testAll: dominion.o testSuite.c
	gcc -o testSuite testSuite.c -g dominion.o rngs.o $(CFLAGS)

interface.o: interface.h interface.c
	gcc -c interface.c -g $(CFLAGS)

runtests: testDrawCard 
	./testDrawCard &> unittestresult.out
	./dominion
	gcov dominion.c >> unittestresult.out
	cat dominion.c.gcov >> unittestresult.out


player: player.c interface.o
	gcc -o player player.c -g dominion.o rngs.o interface.o $(CFLAGS)

#all: playdom player testDrawCard testBuyCard badTestDrawCard runAllTests

all: dominion.o rngs.o interface.o playdom player results badTestDraw

clean:
	rm -f *.o playdom.exe playdom player player.exe *.gcov *.gcda *.gcno *.so *.out testDrawCard testDrawCard.exe ut1 ut2 ut3 ut4 ct1 ct2 ct3 ct4 rtc1 rtc2 rtca

rtc1: randomtestcard1.c dominion.o getCard.o rngs.o interface.o
	gcc -o rtc1 -g randomtestcard1.c dominion.o getCard.o rngs.o interface.o $(CFLAGS)

rtc2: randomtestcard2.c dominion.o rngs.o getCard.o interface.o
	gcc -o rtc2 -g randomtestcard2.c dominion.o rngs.o getCard.o interface.o $(CFLAGS)

rtca: randomtestadventurer.c dominion.o rngs.o getCard.o interface.o
	gcc -o rtca -g randomtestadventurer.c dominion.o rngs.o getCard.o interface.o $(CFLAGS)

randtests: rtc1 rtc2 rtca


ut1: unittest1.c dominion.o rngs.o getCard.o
	gcc -o ut1 -g unittest1.c dominion.o rngs.o getCard.o $(CFLAGS)

ut2: unittest2.c dominion.o rngs.o getCard.o
	gcc -o ut2 -g unittest2.c dominion.o rngs.o getCard.o $(CFLAGS)

ut3: unittest3.c dominion.o rngs.o getCard.o
	gcc -o ut3 -g unittest3.c dominion.o rngs.o getCard.o $(CFLAGS)

ut4: unittest4.c dominion.o rngs.o getCard.o
	gcc -o ut4 -g unittest4.c dominion.o rngs.o getCard.o $(CFLAGS)

unittests: ut1 ut2 ut3 ut4


ct1: cardtest1.c dominion.o getCard.o rngs.o
	gcc -o ct1 -g cardtest1.c dominion.o getCard.o rngs.o $(CFLAGS)

ct2: cardtest2.c dominion.o rngs.o getCard.o
	gcc -o ct2 -g cardtest2.c dominion.o getCard.o rngs.o $(CFLAGS)

ct3: cardtest3.c dominion.o rngs.o getCard.o 
	gcc -o ct3 -g cardtest3.c dominion.o rngs.o getCard.o $(CFLAGS)

ct4: cardtest4.c dominion.o rngs.o getCard.o interface.o
	gcc -o ct4 -g cardtest4.c dominion.o rngs.o getCard.o interface.o $(CFLAGS)

cardtests: ct1 ct2 ct3 ct4

tests: unittests cardtests randtests

results: tests
	./rtc1 &> rtc1_results.out
	gcov randomtestcard1.c -b >> rtc1_results.out
	./rtc2 &> rtc2_results.out
	gcov randomtestcard2.c -b >> rtc2_results.out
	./rtca &> rtca_results.out
	gcov randomtestadventurer.c -b >> rtca_results.out
	./ut1 &> ut1_results.out
	gcov unittest1.c -b >> ut1_results.out
	./ut2 &> ut2_results.out
	gcov unittest2.c -b >> ut2_results.out
	./ut3 &> ut3_results.out
	gcov unittest3.c -b >> ut3_results.out
	./ut4 &> ut4_results.out
	gcov unittest4.c -b >> ut4_results.out
	./ct1 &> ct1_results.out
	gcov cardtest1.c -b >> ct1_results.out
	./ct2 &> ct2_results.out
	gcov cardtest2.c -b >> ct2_results.out
	./ct3 &> ct3_results.out
	gcov cardtest3.c -b >> ct3_results.out
	./ct4 &> ct4_results.out
	gcov cardtest4.c -b >> ct4_results.out       
