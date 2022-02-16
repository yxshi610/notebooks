# C++ Programming for Unreal Game Development

https://www.coursera.org/specializations/cplusplusunrealgamedevelopment

## First Console App in Visual Studio

### Using Doxygen Commenting

`/**`

change the template scripts the Unreal engine uses. since the Epic Games coding standard requires them in the Unreal Engine codebase.

Engine\Content\Editor\Templates

### First Console App

Windows Desktop Wizard.

`// Copyright Yuxing Shi. All Rights Reserved.` in the first line.

### First Unreal Script

the outmost content folder, the same name with the project. -> Maps.

Edit -> Project Settings. Maps & Modes: default as Map0.

File -> New C++ Class -> load Actor template (change name)

compile C++ code before go back to Unreal.

```cpp
// Copyright

#include "PrintFavoriteGames.h"

/**
 * Sets default values
*/
APrintFavoriteGames::APrintFavoriteGames()
{
     // Set this actor to call Tick() every frame.
    PrimaryActorTick.bCanEverTick = false;

}

/**
 * Called when the game starts or when spawned
*/
void APrintFavoriteGames::BeginPlay()
{
    Super::BeginPlay();

    // print favorite games
    UE_LOG(LogTemp, Warning, TEXT("Assetto Corsa"));
}

/**
 * Called every frame
 * @param DeltaTime Game time elapsed during last frame modified by the time dilation
*/
void APrintFavoriteGames::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

}
```
