# Molecular Dynamics

## Pipeline
To run the code properly, start by installing `requirements.txt` by 

```bash
pip install -r requirements.txt
```
In the your virtual environment.

The files `sim.py` and `sim_fast.py` perform the exact same task. however, `sim_fast.py` utilizes a precomputed 
neighbor list for all atoms, this significantly reduces compute time and yields similar results as `sim.py`, therefore `sim_fast.py` is used in all other files in the project. ´sim_fast.py´ is also the point of entry in the project and performs the first task by calculating the auto correlation and the correlation time. Run it by
```bash
python /src/sim_fast.py --y 0.01 --io
```
`--io` saves the results and ´--y´ specifies the damping parameter $\gamma$. Additionally ´--plot´ can be used to plot the results directly and ´--T´ can be used to specify the temperature which has a default value of $300^\circ K$.

To evaluate the Mean-Squared Displacement run `MSD.py`. Note, this code essentially does the same code as `sim_fast.py` over an array of different temperatures, specified by `--points`, thus scaling up the compute time with number of temperature points.
```bash
python src/MSD.py --points 7 --plot --io

```
Runs calculates the MSD for 7 temperatures equally divided across the range $100^\circ K \to 1000^\circ K$, showing the plot and saving the results to JSON.


Expermiments were conducted by running all three major tasks (varying $\gamma$, varying $T$, and varying $a$) a number of times and the averaging the results.