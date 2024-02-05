show databases

#Q1  Import both the .CSV files in Dbeaver under the database name
Sky_Sports

create table group_stage (select *from sql_SkySports_Project16875987300);

select *from group_stage;

create table wc_stats ( select * from sql_skysports_project16875987301);

select *from wc_stats;

#Q2 Write an sql query to show all the UNIQUE team names

select distinct (team)from group_stage;

#Q3 Write an SQL query to show name of team which has rank 1 from group 7

select team from group_stage where 'rank'=1 and 'group'=7;

#Q4 Write an sql query to show count of all teams

select count(team) from group_stage ;

#Q5 Write an SQL query to show matches_played by each team
 select team, matches_played from group_stage;

#Q6 Write an SQL query to show team, percent of wins with respect to matches_played by each team and name the resulting column 
#as wins_percent

select team , wins*100/matches_played from group_stage as wins_percent;

select team , 100*(wins/matches_played) from group_stage as wins_percents;

#Q7 Write an SQL query to show which team has maximum goals_scored and their count

select team , goals_scored from group_stage where goals_scored=(select max(goals_scored) from group_stage);

#Q8 Write an SQL query to show percent of draws with respect to matches_played round of to 2 digits by each team

select team , round ((draws*100/matches_played),2) from group_stage ;

#Q9 Write an SQL query to show which team has minimum goals_scored and their count

select team , goals_scored from group_stage where goals_scored = (select min(goals_scored) from group_stage);

#Q10 Write an SQL query to show percent of losses with respect to
#matches_played by each team in ascending order by losses and
#name the resulting column as losses_percent

select team , losses*100/matches_played as losses_percent from group_stage order by losses_percent asc ;

#Q11 Write an SQL query to show the average goal_difference

select avg(goal_difference) from group_stage gs ;

#Q12 Write an SQL query to show name of the team where points are 0

select team , points from group_stage where points= 0;

#Q13 Write a SQL query to show all data where expected_goal_scored is less than exp_goal_conceded

select *from group_stage where expected_goal_scored < exp_goal_conceded ;

#Q14 Write an SQL query to show data where exp_goal_difference is in between -0.5 and 0.5

select * from group_stage gs where exp_goal_difference  between -0.5 and 0.5;

#Q15 Write an SQL query to show all data in ascending order by exp_goal_difference_per_90

select *from group_stage order by exp_goal_difference_per_90 asc;

#Q16 Write an SQL query to show team which has maximum number of players_used

select  team, players_used from wc_stats where players_used=(select max(players_used) from wc_stats) ;

#Q17 Write an SQL query to show each team name and avg_age in ascending order by avg_age

select team , avg_age from wc_stats order by avg_age asc;

#Q18 Write an sql query to show average possession of teams

select avg(possession) from wc_stats ;

#Q19 Write a SQL query to show team which has played atleast 5 games

select team, games from wc_stats ws where games <=5;

#Q20 Write an SQL query to show all data for which minutes is greater than 600

select * from wc_stats ws where minutes >600;

#Q21 Write an SQL query to show team, goals, assists in ascending order by goals

select team , goals , assists from wc_stats ws order by goals asc;

Q22 Write an SQL query to show team, pens_made, pens_att in descending order by pens_made

select team , pens_made , pens_att from wc_stats ws order by pens_made desc;

#Q23 Write an SQL query to show team, cards_yellow, cards_red where cards_red is equal to 1 in ascending order by cards_yellow

select team , cards_yellow , cards_red from wc_stats ws where cards_red =1 order by cards_yellow asc;

#Q24 Write an SQL query to show team, goals_per90, assists_per90, goals_assists_per90 in descending order by goals_assists_per90

select team, goals_per90 ,assists_per90 , goals_assists_per90 from wc_stats ws order by goals_assists_per90 desc;

#Q25 Write an SQL query to show team, goals_pens_per90, goals_assists_pens_per90 in ascending order by
#goals_assists_pens_per90

select team , goals_pens_per90, goals_assists_pens_per90 from wc_stats ws order by goals_assists_pens_per90 asc;

#Q26 Write an SQL query to show team, shots, shots_on_target, shots_on_target_pct where shots_on_target_pct is less than 30
#in ascending order by shots_on_target_pct

select team,shots, shots_on_target, shots_on_target_pct from wc_stats ws where shots_on_target_pct <30 order by shots_on_target_pct asc;

#Q27 Write an SQL query to show team, shots_per90, shots_on_target_per90 for team Belgium

select team, shots_per90 , shots_on_target_per90 from wc_stats ws where team='Belgium';

#Q28 Write an SQL query to show team, goals_per_shot, goals_per_shot_on_target, average_shot_distance in descending 
#order by average_shot_distance

select team, goals_per_shot,goals_per_shot_on_target, average_shot_distance from wc_stats ws order by average_shot_distance desc;

#Q29 Write an SQL query to show team, errors, touches for which errors is 0 and touches is less than 1500

select team, errors , touches from wc_stats ws where errors=0 and touches < 1500;

#Q30 Write an SQL query to show team, fouls which has maximum number of fouls

select team, fouls from wc_stats ws where fouls = (select max(fouls) from wc_stats);

#Q31 Write an SQL query to show team, offisdes which has offsides less than 10 or greater than 20

select team, offsides from wc_stats ws where offsides <10 or offsides >20;

#Q32 Write an SQL query to show team, aerials_won, aerials_lost, aerials_won_pct in descending order by aerials_won_pct

select team, aerials_won, aerials_lost , aerials_won_pct from wc_stats ws order by aerials_won_pct desc;

#Q33 Write an SQL query to show number of teams each group has!

select 'group' , count(team) from group_stage gs  group by 'group';

#Q34 Write a SQL query to show team names group 6 has
select team , `group`  from group_stage gs where 'group'= 6;

#Q35 Write an SQL query to show Australia belongs to which group

select team , `group`  from group_stage gs where team = 'Australia';

#Q36 Write an SQL query to show group, average wins by each group

select `group` , avg(wins) from group_stage gs group by `group`;

#Q37 Write an SQL query to show group, maximum expected_goal_scored by each group in ascending order by expected_goal_scored

select `group`, max(gs.expected_goal_scored) as max_exp_goalS_scored from group_stage gs 
group by `group` order by max_exp_goals_scored asc;

#Q38 Write an SQL query to show group, minimum exp_goal_conceded by each group in descending order by exp_goal_conceded

select `group` , min(exp_goal_conceded) as min_exp_goal_conceded from group_stage gs 
group by `group`  order by min_exp_goal_conceded desc;

#Q39 Write an SQL query to show group, average exp_goal_difference_per_90 for each group in ascending order
#by exp_goal_difference_per_90

select `group` , avg(exp_goal_difference_per_90) as avg_exp_goal_difference_per_90 from group_stage gs 
group by `group` order by avg_exp_goal_difference_per_90 asc;

#Q40 Write an SQL query to show which team has equal number of goals_scored and goals_against

select team , goals_scored , goals_against  from group_stage gs where goals_scored = goals_against ;

#Q41 Write an SQL query to show which team has maximum players_used

select team, players_used from wc_stats ws where players_used  = ( select max(players_used) from wc_stats ws );

#Q42 Write an SQL query to show team, players_used, avg_age, games, minutes where minutes lessthan 500 and greater than 200
 
select team, players_used, avg_age, games , minutes from wc_stats ws where minutes between 200 and 500;

#Q43 Write an SQL query to show all data of group_stats in ascending order BY points

select *from group_stage gs order by points asc;

#Q44 Write an SQL query to show ALL UNIQUE team in ascending order by team

select distinct(team) from wc_stats ws  order by team asc;

#Q45 Write an SQL query to show average avg_age of each group and arrange it in descending order by avg_age.

select `group` , avg(avg_age) as avg_avg_age from wc_stats ws inner join group_stage gs on ws.team=gs.team 
group by `group` order by avg_avg_age desc;

#Q46 Write an SQL query to show sum of fouls for each group and arrange it in ascending order by fouls.

select `group` , sum(fouls) as total_fouls from wc_stats ws inner join group_stage gs on ws.team = gs.team 
group by `group` order by total_fouls asc;

#Q47 Write an SQL query to show total number of games for each group and arrange it in descending order by games.

select `group` , sum(games) as sum_games from wc_stats ws inner join group_stage gs on ws.team = gs.team 
group by `group` order by sum_games desc;

#Q48 Write an SQL query to show total number of players_used for each group and arrange it in ascending order by players_used

select `group` , sum(players_used) as sum_players_used from wc_stats ws inner join group_stage gs on ws.team=gs.team 
group by `group` order by sum_players_used asc; 

#Q49 Write an SQL query to show total number of offsides for each group and arrange it in ascending order by offsides.

select `group`, sum(offsides) as total_offsides from wc_stats ws inner join group_stage gs on ws.team = gs.team 
group by `group` order by total_offsides asc;

#Q50 Write an SQL query to show average passes_pct for each group and arrange it in descending order by passes_pct.

select `group` , avg(passes_pct) as avg_passes_pct from wc_stats ws inner join group_stage gs on ws.team = gs.team 
group by `group` order by avg_passes_pct desc;

#Q51 Write an SQL query to show average goals_per90 for each group and arrange it in ascending order by goals_per90.

select `group` , avg(goals_per90) as avg_goals_per90 from wc_stats ws inner join group_stage gs on ws.team = gs.team 
group by `group` order by avg_goals_per90 asc;

#THE END.
