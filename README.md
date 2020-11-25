# Devops Challenge 1

The below describes a problem statement, make sure to read all of the instructions in this readme before you start

- We need to create an application :computer: that imports data when a new file is received in a specific folder 
- Prior to import
    - Do validations on the files as they are received :hammer_and_wrench:
    - Discard any files that the `recordcount` or `qtysum` does not add up
    - Ensure that the same file is not processed twice :triangular_flag_on_post:  
      If a previously processed file is requeued then it should be skipped (look at `transmissionsummary.id`)
- During import
    - Insert the data into a DB table
- After import
    - Print some statistics after each record import is completed successfully
        - Print an aggregate of L3 categories and total qty stock per store
        - Move the file to a different folder after they have completed processing
        


## Sample output
Below is an example of the expected output from the running app
```
Processing drop-1.json
Completed drop-1.json
Power Tools - Artarmon - 20
Power Tools - Notting Hill - 44
Power Tools - Notting Hill - 44
Power Tools - Oakleigh - 7

Processing drop-2.json
Discarding drop-2.json, incorrect qtysum
Power Tools - Artarmon - 20
Power Tools - Notting Hill - 44
Power Tools - Notting Hill - 44
Power Tools - Oakleigh - 7

Processing drop-3.json
Completed drop-3.json
Power Tools - Artarmon - 21
Power Tools - Notting Hill - 44
Power Tools - Notting Hill - 44
Power Tools - Oakleigh - 12
Tiles - Oakleigh - 1

```
- If you requeue a file the expected output is
```
Processing drop-1.json
Skipped drop-1.json
```



## Solution & design
- Use docker containers to host and run the above
- Use different containers for the app and db
- Build your importer app using .NET Core
- Ensure we can pass the folder names into the container
- Sample data files can be (seen here)[/Sample Data]
- Write a SQL query to calculate the stats

## Deliverables:

- Spend as little or as much time as you like :watch:
- The output of the efforts :exclamation: *must* be committed back into a Public Repo in Github and the URL shared back for review.
Proving your code works via unit testing is highly encouraged


