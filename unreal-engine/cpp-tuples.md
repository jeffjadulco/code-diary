# Tuples in UE4 C++

## Notes
- Syntax and examples
```cpp
// Declaration
TTuple<type1, type2> Foo { value1, value2 };
TTuple<type1, type2, type3> Bar { value1, value2, value3 };

// Assignment
Foo = MakeTuple(value1, value2);
Bar = MakeTuple(value1, value2, value3);

Foo.Key = value1;
Foo.Value = value2;

Bar.Get<0>() = value1;
Bar.Get<1>() = value2;
Bar.Get<2>() = value3;

// Access. 2-Tuple uses the TPair api
auto FooValue1 = Foo.Key;
auto FooValue2 = Foo.Value;

// Access by index
auto BarValue1 = Bar.Get<0>();
auto BarValue2 = Bar.Get<1>();
auto BarValue3 = Bar.Get<2>();
```
```cpp
TTuple<FString, float> USampleClass::GetRegionPing()
{
  // ...
  const FString Region = FString("");
  const float Ping = 0;
  // ...
  return MakeTuple(Region, Ping);
}

// Sample usage
TTuple<FString, float> MyRegionPing = GetRegionPing();
float MyPing = MyRegionPing.Value;
float MyRegion = MyRegionPing.Key;
```


## Experiences
- Need to find a way to represent data (for a single use only) with more than 1 property without defining a new struct
- Why? Don't want to bloat the codebase by defining a new struct for a single use only. In case, an api change is needed to use it in other classes or expose it to blueprints, then defining a new struct or class is a better choice.

## Resources
- https://www.youtube.com/watch?v=FepPWr7YFlY
- https://github.com/EpicGames/UnrealEngine/blob/4.22.3-release/Engine/Source/Runtime/Core/Public/Templates/Tuple.h
