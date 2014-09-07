(a full spec and mockup is in the root directory)

we need a slider/progressbar that will control and display a dynamic timeline that represents the work on stages within a given timeframe.

basic flow:

our user has a set timeframe for the timeline (start_date until end_date)
then, the user choose stage_1_start_date and finish_date
after that, the user is able to edit all fields and set the dates.
finally, after approval, it should:
 show the selected dates on a timeline, with the count of days for each stage.
show the progress (which stage are we on) by filling the bar
flow in short:
choose start and finish --> choose the rest of the timeline dates -> approve and show progress

this directive should bind to the timeline object that holds:

* start_date (optional, defaults to today), shouldn't change
* end_date, shouldn't change
* dates_array:  [stage_1_start_date, stage_2_start_date, .., stage_n_start_date, finish_date] (each cell holding a date or null if not yet set). 
a hash could work also.
* completed_stage: 0<=integer<=n. the number completed stages.the progress bar will be filled accordingly.
* mode: INITIAL (only start and finish dates are editable), EDIT (all dates are editable), and DISPLAY (present the timeline and progress)

client side validation: 
all dates should be between start_date and end_date
if n<m then stage_n_start_date < stage_m_start_date

extra points:

we need it to work for 3 stages, which means we need 4 handles (stage_1_start_date, stage_2_start_date, stage_3_start_date, finish_date).
we would love to get a generic version that supports N stages with N+1 handles.
