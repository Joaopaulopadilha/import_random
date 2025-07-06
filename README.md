# JP Random Module

Simple and intuitive random number generation for the JP programming language.

## Installation

```bash
jp install random
```

## Quick Start

```jp
import random

// Roll a dice
dice = randInt(1, 6)
print("🎲 You rolled:", dice)

// Flip a coin
if randBool() {
    print("🪙 Heads!")
} else {
    print("🪙 Tails!")
}

// Random chance event
if randBool(0.1) {  // 10% chance
    print("💎 You found treasure!")
}
```

## Functions

### `randInt(min, max)`
Random integer between min and max (both inclusive).

```jp
dice = randInt(1, 6)        // Dice roll (1-6)
percent = randInt(0, 100)   // Percentage (0-100)
damage = randInt(10, 20)    // Game damage (10-20)
```

### `randFloat(min, max)`
Random floating point number between min and max.

```jp
chance = randFloat(0.0, 1.0)      // Probability (0.0-1.0)
temp = randFloat(-10.5, 35.2)     // Temperature
speed = randFloat(0.5, 2.0)       // Speed multiplier
```

### `randBool(probability?)`
Random true/false. Optional probability parameter (default 0.5 = 50%).

```jp
coin = randBool()           // 50/50 chance
rare = randBool(0.01)       // 1% chance  
common = randBool(0.8)      // 80% chance
```

### `randSeed(seed)`
Set seed for reproducible random numbers (useful for testing).

```jp
randSeed(12345)             // Set seed
dice1 = randInt(1, 6)       // Always same sequence
dice2 = randInt(1, 6)       // when using same seed
```

## Examples

### Dice Game
```jp
import random

print("🎲 Rolling two dice...")
d1 = randInt(1, 6)
d2 = randInt(1, 6)
total = d1 + d2

print("Dice 1:", d1)
print("Dice 2:", d2)
print("Total:", total)

if total == 7 {
    print("🎉 Lucky seven!")
}
```

### Weather System
```jp
import random

// Simple weather with chances
rain_chance = randFloat(0.0, 1.0)

if rain_chance < 0.2 {
    print("☀️ Sunny day!")
} else {
    if rain_chance < 0.6 {
        print("☁️ Cloudy weather")
    } else {
        print("🌧️ It's raining!")
    }
}
```

### Game Loot System
```jp
import random

print("🎮 Opening treasure chest...")

// Different rarity chances
loot_roll = randFloat(0.0, 1.0)

if loot_roll < 0.01 {          // 1% chance
    print("🌟 LEGENDARY item!")
} else {
    if loot_roll < 0.1 {       // 9% chance  
        print("💜 EPIC item!")
    } else {
        if loot_roll < 0.3 {   // 20% chance
            print("💙 RARE item!")
        } else {               // 70% chance
            print("⚪ Common item")
        }
    }
}

// Random gold amount
gold = randInt(10, 100)
print("💰 Found", gold, "gold!")
```

### Number Guessing Game
```jp
import random

print("🔢 Guess the number (1-10)!")

secret = randInt(1, 10)
guess = 5  // Simulate a guess

print("You guessed:", guess)

if guess == secret {
    print("🎉 Correct! You win!")
} else {
    print("❌ Wrong! The number was:", secret)
}
```

## Requirements

- C++ compiler with `<random>` support (C++11 or later)
- No external dependencies

## Notes

- Uses high-quality Mersenne Twister generator (`std::mt19937`)
- Automatically seeded with `std::random_device`
- Thread-safe within single program execution
- `randInt` includes both min and max values
- `randFloat` includes min but excludes max (standard behavior)

## License

MIT License
