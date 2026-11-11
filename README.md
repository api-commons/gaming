# Gaming

The common game-platform vocabulary -- the games, the players and their profiles, the leaderboards and achievements they earn, and the matches they play -- distilled from the APIs that already exist. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Gaming, Video Games, Game Development, Game Servers, Esports, Game Backend in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| game_title | 15 | 14 | name 57%, id 50% | games 13, game 4, titles 3 |
| player_profile | 7 | 6 | id 67%, player_id 67%, name 50%, username 50% | players 6, player 2 |
| leaderboard | 15 | 12 |  | leaderboards 8, leaderboard 7, rankings 1 |
| achievement | 5 | 5 | name 80%, description 60%, id 60% | achievements 5 |

Cohort: 73 providers with harvested OpenAPI, 26 crosswalks. Of the providers exposing a game_title: 33% create, 93% list, 40% fetch, 7% update, 7% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- Game platforms agree on the game title's id and name, and on player profiles' id, name and username; player_id appears beside id at the same providers, the platform's key next to the game's own.
- Leaderboards are widely exposed but share no core: rank reaches 42% and score 33%. Achievements agree on name, description and id.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- game_title, player_profile and game_match carry role names because game, player and match collide with the sports context.
- Matches and lobbies were measured and dropped; each game-server platform shapes a session its own way.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
