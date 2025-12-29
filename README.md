# CSAS_Curling_Data_Challenge

Strategic Timing
When is the optimal time to deploy the power play? At what score differential and in which end should teams use this advantage?
How does power play effectiveness vary by opponent? Can strategies be customized based on the opposing team's tendencies?
Shot Selection & Execution
What are the most effective opening sequences? Should the first shot come around the guard to the open side, or are there better approaches?
How do the first 3 shots correlate with end outcomes?
What's the relationship between shot quality and scoring? How often does drawing under a guard result in zero points scored?
Comparative Analysis
Why do some teams score significantly more on power plays? For example, what makes Great Britain (Bruce Mowat) more successful than Italy on power plays?
How often can teams realistically expect to score 3+ points? What conditions make big scores possible?
Defensive Considerations
How should teams defend against power play attacks? What defensive setups minimize opponents' scoring opportunities?
Risk vs. reward analysis. When should teams "punt" an end versus fighting for a steal?


Student Deliverables Could Include:

Power play timing optimization model
Shot selection probability calculator (i.e., likelihood of scoring or giving up 0, 1, 2, 3, etc., points in the end based on the current stone positions and probability of success of upcoming shot options)
Team-specific strategy recommendations (based on considering the teams who will be competing at the Olympics)
Defensive positioning guidelines
Performance benchmarking across international teams


Grading Criteria

How original is the analysis?
How applicable is the analysis?
How appropriate were the methods used?
How well did you communicate your findings? This includes both written text and visualizations. How did the use of facts, data-supported narratives, anecdotes etc. enhance your storytelling?


Datasets

Competition.csv:
CompetitionName – Name of the competition.
Place – City/Country where the competition was competed.
Venue – Venue where the competition was competed.
CompetitionID – Unique ID for the competition.

Competitors.csv:
CompetitionID – ID for the competition (from Competitions.csv).
TeamID – ID for the team. Note: Team IDs across different competitions are associated with nations, not necessarily the individuals on that team.
NOC – National Olympic Committee, the nation of the competing team.
Reportingname – Name of the competing athlete (LAST NAME First Name) .

Ends.csv:
CompetitionID – ID for the competition (from Competitions.csv).
SessionID – ID of the draw/round for the match.
GameID - ID for the match. Note: A unique ID for a match can be made from a combination of Competition, Session and Game IDs.
TeamID – ID for the team (from Teams.csv).
EndID – ID for an end of the match.
Result – The points scored by that team in the end.
PowerPlay – A flag for when a team uses their power play in an end. A value of 1 corresponds to pre-placed stones being moved to the right side, 2 being pre-placed stones are moved to the left side. An empty value means the team is not using their power play.

Games.csv:
CompetitionID - ID for the competition (from Competitions.csv).
SessionID - ID of the draw/round for the match.
GameID - ID for the match. A unique ID for a match can be made from a combination of Competition, Session and Game IDs.
GroupID – In competitions where teams are split into groups for play, the ID of the group for the teams in this match.
Sheet – The name of the sheet on which the match is played.
NOC1 – National Olympic Committee of the first competing team.
NOC2 - National Olympic Committee of the second competing team.
ResultStr1 – Final Score of Team 1.
ResultStr2 – Final Score of Team 2.
LSFE – Last Stone First End. This column indicates which team threw the last stone in the first end of the match. In curling parlance, this is called starting with “the hammer”. A 0 value means that NOC2 threw the last stone in the first end, a 1 means that NOC1 threw last.
Winner – Indicates the winning team. 0 indicates that NOC2 won the match, 1 indicates that NOC1 won the match.
TeamID1 – ID for the team corresponding to NOC1 and ResultsStr1 (from Teams.csv).
TeamID2 - ID for the team corresponding to NOC2 and ResultsStr2 (from Teams.csv).

Stones.csv:
CompetitionID – ID of Competition in which match was competed (from Competitions.csv)
SessionID – ID of the draw/round for the match.
GameID – ID for the match. A unique ID for a match can be made from a combination of Competition, Session and Game IDs.
EndID – The end in which the shot is taking place.
ShotID – ID for the shot. Within a particular match and end, shots occur in ascending order of the ShotID values. (i.e. lower ShotIDs are thrown first)/
TeamID – ID for the Team (from Teams.csv).
PlayerID – ID for the player taking the shot (1 or 2).
Task – The type of shot that the player is throwing, or the objective of the shot. Details to come.
"0": "Draw"
"1": "Front"
"2": "Guard"
"3": "Raise / Tap-back"
"4": "Wick / Soft Peeling"
"5": "Freeze"
"6": "Take-out"
"7": "Hit and Roll"
"8": "Clearing"
"9": "Double Take-out"
"10": "Promotion Take-out"
"11": "through"
"13": "no statistics"
Handle – The turn of the stone as it is thrown. A 0 value means the shot is turning clockwise, a 1 indicates counterclockwise.
Points – An assessment of the execution of the shot, ranging from 0 to 4. A 4-point shot is one that has been ascertained to have been perfectly executed to the player’s intention, while a 0 is a shot that totally failed in its intended result. Note that these points are not the same as points awarded to teams after ends, but simply an evaluation of a shot’s effectiveness.
TimeOut – Binary variable for whether a time out was called before the shot.
Stone_{i}_x – The x position of stone i on the sheet, after the stone for the row has been thrown. Stones can take x values in (0,1500). The value 4095 is a sentinel value indicating that the stone has been knocked off the sheet and is no longer in play. The value 0 indicates that the stone has not yet been thrown in this end.
Stone_{i}_y – The y position of stone i on the sheet, after the stone for the row has been thrown. Stones can take y values in (0,3000). Again, the value 4095 indicates the stones have been knocked off the sheet and aren’t in play, and the value 0 indicates the stones have not yet been thrown.
A Note on stones: Stone i does not necessarily correspond to ShotID i. The first six stones are the stones of the team that is throwing first in the end, while stones 7-12 are for the other team in that end. Stone_1 and Stone_7 are the pre-placed stones, and teams throw the rest of their stones in order. For example, a team going first in an end would have stones 2-6 and throw them in ascending order.

A curling sheet is marked by several important lines and positions that define gameplay and scoring.

Centerline (x = 750): Divides the sheet lengthwise and serves as a reference axis for all play.
Backline (y = 200): Marks the rear edge of the house; stones completely crossing it are out of play.
Hogline (y = 2900): Indicates the line that stones must completely cross to remain in play and where players must release the stone before delivery.
Button (x = 750, y = 800): Represents the center of the house, used as the reference point for scoring.

Teams.csv:
CompetitionID - ID for the competition (from Competitions.csv).
TeamID - ID for the Team (from Teams.csv).
NOC - National Olympic Committee, the nation of the competing team.
Name – Name of the country corresponding to NOC abbreviation.
