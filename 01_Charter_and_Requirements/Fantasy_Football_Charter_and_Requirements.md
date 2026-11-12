# Fantasy Football Recommender

## 1. Business Case

Most fantasy football advice assumes you already know football. Ranking sites,
podcasts, and social media all talk in stats and terminology that a new player
won't follow. So beginners either copy rankings without understanding them or
lose interest and stop setting their lineup.

Cost is mostly team time, plus hosting and any data fees. Expected benefit is
ad and affiliate revenue from an audience nobody else is serving well. Gambling
and betting are deliberately excluded: they bring state-by-state licensing, age
verification, and app store restrictions, so that's a separate decision after v1.

## 2. Project Description

A beginner-friendly fantasy football recommendation and analysis **web app**
designed for **"people who don't know ball."** It takes fantasy football data
and turns it into clear recommendations with plain-English explanations, so
users can make better lineup and roster decisions.

Being beginner-friendly is a hard requirement, not just a tone thing. Any stat
or football term shown to the user has to come with a plain-English explanation
of what it means.

## 3. Objectives

Numbers below are first-pass targets and still need to be confirmed. O1 is
checked by backtesting prior seasons and tracking during the season. O2 and O3
are checked with real beginner testers in the M6 beta.

| # | Objective | How it's measured |
|---|---|---|
| O1 | Beat the obvious baseline | Start/sit picks beat the platform's default projections on 55% or more of the close calls over a 17-week season |
| O2 | Cut the time it takes to manage a team | Someone who has never played fantasy can set a full valid lineup in under 3 minutes |
| O3 | Make every recommendation understandable | Every recommendation comes with a 1-2 sentence reason, with no unexplained football jargon |
| O4 | Keep beginners around | 40% of week 1 users come back in week 2, 25% still active by week 8 |
| O5 | Stay reliable | The app stays up and the weekly data refresh keeps working for a full season |
| O6 | Connect to real leagues | Roster integration works end to end for at least one platform, with manual entry as the fallback |

## 4. Scope

### In scope

- Player and matchup analysis
- Start/sit recommendations
- Lineup optimization
- Waiver wire recommendations
- Trade analysis
- Injury and player-status insights
- Beginner-friendly explanations of recommendations
- Fantasy team/roster integration or manual entry

### Out of scope

- Non-standard league formats
- Daily fantasy and any betting features
- Live in-game updates (batch only)
- Anything outside the US, and any sport other than the NFL
- Native mobile apps (web only for v1)

## 5. Deliverables and Milestones

| # | Deliverable | Target |
|---|---|---|
| M1 | Data ingestion pipeline and player/stat schema | TBD |
| M2 | Recommendation engine (start/sit, lineup optimization) | TBD |
| M3 | Explanation layer (generating the plain-English reasons) | TBD |
| M4 | Web UI with manual roster entry | TBD |
| M5 | Integration with at least one major fantasy platform | TBD |
| M6 | Closed beta with beginner testers | TBD |

## 6. Stakeholders

| Stakeholder | Why they matter |
|---|---|
| Beginner fantasy players | The main users. Success is measured against them |
| Experienced players and league commissioners | Not the target user, but they're the ones who recruit beginners into leagues |
| Data and platform providers | Control whether the underlying data is available and on what terms |
| Ad and affiliate partners | Revenue side, and they put constraints on the UI |
| Project team (us) | Sponsor, PM, and the people building it |

## 7. Assumptions and Constraints

### Assumptions

- Free/open data sources stay available, accurate, and updated every game week
- Weekly batch updates are good enough for v1, users don't need live in-game data
- Users will either connect their league account or type in a roster manually
- Standard scoring formats used by most casual leagues cover the target users

### Constraints

- US only, for both data and legal reasons
- Batch data ingestion, probably weekly, lined up with the NFL game week
- Only some platforms expose a public API, so manual roster entry is needed as
  a fallback

## 8. Risks

| # | Risk | Impact | What to do about it |
|---|---|---|---|
| R1 | NFL/player stat licensing or scraping terms get violated | High, kills the whole thing | Build on openly licensed data sources, get a legal review before charging anyone money |
| R2 | Roster integration with a major platform is blocked or breaks | Medium, fewer users can connect | Ship one platform plus manual entry first, treat the rest as a stretch goal |
| R3 | Recommendations don't beat the baseline (O1) | High, there's no product without this | Backtest against a couple of prior seasons before launch, treat O1 as a go/no-go |
| R4 | Gambling revenue drags in state-by-state licensing | High, legal and app store exposure | Left out of v1, see section 1 |
| R5 | Explanations are accurate but still confusing to beginners | Medium, undercuts the whole point | Test O3 with non-experts during the M6 beta, not after launch |

## 9. Notes

Current candidates behind the general terms above. These are working
assumptions, not commitments, and can be dropped once decisions are made.

- Data sources: nflverse for open, licensed stats; Sleeper for platform data
- Platform integration: Sleeper first, since ESPN and Yahoo have no public
  fantasy API
- Scoring formats: PPR and half-PPR redraft
- Excluded league formats: dynasty, keeper, auction
- Excluded features: daily fantasy (DFS), betting

## 10. Requirements

### Functional Requirements

- The system shall allow users to import and refresh their roster and league settings from at least one supported fantasy football platform without manually entering individual players.
- The system shall support manual roster entry and editing as an alternative when integration is unavailable or not preferred.
- The system shall automatically retrieve and update NFL player statistics and status information from supported external data sources.
- The system shall store current NFL player information, including position, team, fantasy statistics, and injury status.
- The system shall update player statistics on a weekly basis during the NFL season.
- The system shall allow a user to select two or more players and receive a start/sit recommendation.
- The system shall recommend a valid starting lineup based on the players available on the user's roster.
- The system shall provide injury and player status information when it may affect a recommendation.
- The system shall provide a plain English explanation with every recommendation.
- The system shall explain any football statistic or term shown to a beginner user.
- The system shall support standard fantasy football scoring formats used by the targeted leagues.

### Non-Functional Requirements

- The web application shall be usable on desktop and mobile web browsers.
- Each recommendation shall include a 1-2 sentence explanation.
- User facing explanations shall not contain unexplained fantasy football terminology.
- The system should return recommendations within 15 seconds under normal operating conditions.
- The application shall remain available throughout the NFL season except during planned maintenance.
- The weekly player-data update process shall complete successfully before recommendations for the upcoming game week are generated.
- The system shall handle missing or unavailable player data without crashing.
- User roster information shall be stored securely.
- The application shall provide clear error messages when roster data, player data, or an external platform connection cannot be retrieved.

### Data Requirements

- The system shall maintain a unique record for each NFL player.
- Each player record shall include, at minimum:
  - Player name
  - NFL team
  - Position
  - Fantasy points
  - Relevant season statistics
  - Injury/status information
- Historical player performance shall be retained when needed for recommendation calculations and backtesting.
- The system shall associate each player's statistics with the correct NFL week and season.
- The recommendation engine shall use the most recent available player data when producing recommendations.

### Business / Success Requirements

- A beginner fantasy football user should be able to set a complete valid lineup in under 3 minutes.
- 100% of recommendations shall include a beginner-friendly explanation.
- The project shall support at least one fantasy football platform integration by the targeted release milestone.
- The system shall continue completing its scheduled weekly data refresh throughout the NFL season.
