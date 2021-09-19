Brewing a cup of coffee

---

Objective:
Make a cup of coffee.

Plain text steps:
1. Determine whether coffee pot is plugged in
2. Check water level of coffee pot
3. Open lid of coffee pot
4. Fill water reservoir with enough water for a cup of coffee
5. Put coffee filter in filter basket
6. Fill filter with coffee grounds
7. Close lid
8. Press power switch
9. Wait for beep
10. Pour coffee into cup

## Objects:

User

    wantsCoffee (boolean; default: true)

CoffeeMaker

    isPluggedIn (boolean; default: true)
    lidIsOpen (boolean; default: false)
    isBrewing (boolean; default: false)
    finishedBrewing (boolean; default: false)

CoffeePot
    holdsCoffee - (boolean; default: false)

coffeeFilter
    containsCoffeeGrounds (integer; default: 0)

filterBasket
    hasCoffeeFilter (boolean; default: false)
    hasEnoughCoffeeGrounds (boolean; default: false)

waterReservoir

    waterInTank (integer; default: 0)

water

catMug

    containsCoffee (boolean; default: false)

cupOfCoffee


## Functions:

User
    determineCoffeeMakerPluggedIn
    plugInCoffeeMaker - toggle isPluggedIn
    wait - waits until finishedBrewing = true

coffeeMaker
    toggleLid - set isOpen to true/false
    pressPowerSwitch - toggles isBrewing to true
    beep - alerts user that isBrewing has ended

coffeePot
    pourCoffee - creates cupOfCoffee object with catMug

filterBasket
    insertCoffeeFilter - toggle coffeeFilterInserted to true
    fillWithCoffeeGrounds - toggles hasEnoughCoffeeGrounds to true

waterReservoir
    displayWaterLevel - determines whether water is enough to make coffee
    addWater - add water to waterReservoir

catMug

---

PROGRAM

    INIT 

        CREATE user
        CREATE coffeeMaker
        CREATE coffeePot
        CREATE coffeeGrounds
        CREATE waterReservoir
        CREATE water
        CREATE coffeeFilter
        CREATE switch
        CREATE catMug



    IF wantsCoffee(true)
        determineCoffeeMakerPluggedIn()

        IF isPluggedIn = false
            plugInCoffeeMaker()
        ENDIF

        checkWaterLevel()

        toggleLid()

        WHILE water < enough
            addWater until water >= enough

        insertCoffeeFilter()
        fillWithCoffeeGrounds()
        
        IF isPluggedIn = true 
        AND hasEnoughCoffeeGrounds = true 
        AND water > enough
            toggleLid()
            pressPowerSwitch()
            coffeeMaker.brew()

            WHILE coffeeMaker isBrewing(true)
                User.wait()
        
            IF finishedBrewing = true
                holdsCoffee = true
                beep()
                pourCoffee(catMug)
                CREATE cupOfCoffee

        END