# NHSRwaitinglistsimulator

This repository is a work in progress.

The aim of the repository is to provide the functionality to simulate waiting 
lists under user provided assumptions. The main function is the wl_simulator
which has the following inputs:

    - start_date - the first day to be simulated (this should be in date format)
    - end_date - the final day to be simulated (this should be in date format)
    - demand - the arrival rate of referrals per unit of time 
    - capacity - the number of removals from the waiting list per unit of time 
    - waiting_list - the initial waiting list if available. If not available use NULL.
    - timebase - the unit of time used in defining demand and capacity. 
            This could be  "day","week","month","quarter" or "annual" and is converted to
            days within the code.
    - withdrawal_prob - the probability a waiter leaves the waiting list without
            treatment for example a reneg or death.

Outputs: 
    - Single experiment - a data frame of clock starts (referrals) and clock stops (removals)
        This data frame can be summarised using the function wl_queue_size() to give the queue
        length each day of the simulation.

To run an example: 

sim <- wl_simulator(start_date = "2026-04-01"
               , end_date = "2026-07-01"
               , demand = 10
               , capacity = 11
               , waiting_list = NULL
               , timebase = "week"
               , withdrawal_prob = NA_real_)



Acknowledgements: This code expands upon code initially written in the NHSwaitinglist CRAN package https://github.com/nhs-r-community/NHSRwaitinglist