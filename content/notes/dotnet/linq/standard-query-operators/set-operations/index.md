---
title: notes > dotnet > linq > standard query operators > set operations
date: 2022-11-08T20:37:38-0700
draft: false
---
Set operations are query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate sets.

# Methods
| Method          | Description                                                            | Query expression |
| --------------- | ---------------------------------------------------------------------- | ---------------- |
| `Distinct(By)`  | Removes duplicate values from a collection                             | N/A              |
| `Except(By)`    | Returns the elements of one collection that do not appear in the other | N/A              |
| `Intersect(By)` | Elements that appear in each of two collections                        | N/A              |
| `Union(By)`     | Unique elements that appear in either of two collections               | N/A              |

The `*By` methods take a keySelector which is used as the comparative discriminator of the source type.
```cs
record Planet(string Name, PlanetType Type, int OrderFromSun)
{
    public static readonly Planet Mercury = new(nameof(Mercury), PlanetType.Rock, 1);
    public static readonly Planet Venus = new(nameof(Venus), PlanetType.Rock, 2);
    public static readonly Planet Earth = new(nameof(Earth), PlanetType.Rock, 3);
    public static readonly Planet Mars = new(nameof(Mars), PlanetType.Rock, 4);
    public static readonly Planet Jupiter = new(nameof(Jupiter), PlanetType.Gas, 5);
    public static readonly Planet Saturn = new(nameof(Saturn), PlanetType.Gas, 6);
    public static readonly Planet Uranus = new(nameof(Uranus), PlanetType.Liquid, 7);
    public static readonly Planet Neptune = new(nameof(Neptune), PlanetType.Liquid, 8);
    public static readonly Planet Pluto = new(nameof(Pluto), PlanetType.Ice, 9);
}

enum PlanetType { Rock, Ice, Gas, Liquid };

Planet[] planets =
{
    Planet.Mercury, Planet.Venus, Planet.Earth, Planet.Mars, Planet.Jupiter,
    Planet.Saturn, Planet.Uranus, Planet.Neptune, Planet.Pluto
};

foreach (Planet planet in planets.DistinctBy(p => p.Type)) // Discriminate by PlanetType
{
    …
}

// A "keySelector" can be made a method (in this case, a local method):
static string PlanetNameSelector(Planet planet) => planet.Name;

foreach (Planet planet in planets.ExceptBy(
    morePlanets.Select(PlanetNameSelector, PlanetNameSelector)
    )
    {
        …
    }
```
