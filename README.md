# STRIKE A POSE! 
**Predictive Body Pose Classification via Sequential Neural Network Analysis in a Motion-Controlled Videogame**

<p align="center">
    <img src="https://github.com/alx-sch/STRIKE_A_POSE_Body_Pose_Classification_Game/assets/134595144/efd8d989-79a2-48e5-9f77-0006680ff04d" alt="dancer.png" style="width: 250px;" />
</p>

## Intro 
"**STRIKE A POSE!**" is an interactive, motion-controlled videogame.   

It's a fun workout challenge using body pose classification, in which to follow along with various exercises:   
From squats to standing, hiding, making an X, or striking a unique pose of your own, you'll work up a sweat! 🏋️   

You have the flexibility to adjust the number of rounds and the time between poses for an extra challenge.    

Data collection, model training, and the game script are modularized, making it easy to customize to meet your unique workout needs. 💪  

---

### Demo
Turn the audio on! 🎧  
Check out the demonstration video in better quality [here](https://www.loom.com/share/c715db6d054c44cab8a703be838f9201?sid=b5d8c26a-da8b-4349-9043-285fca207493).

https://github.com/alx-sch/STRIKE_A_POSE_Body_Pose_Classification_Game/assets/134595144/bcffa499-bdbe-4177-996d-abcd805d37d4

---

### System Requirements

- The game takes around **∼2.4 GB disk space** due to the encapsulated virtual environment the game is running in, but can be easily deleted completely.
  
- Make sure that **Python 3**, **Git**, and the **HDF5 C Library** (for managing large datasets required by TensorFlow) are installed on your system.
 
     1. **Check Installation Status**

        Run these commands to verify the packages are available:
        
        ```bash
        git --version
        python3 --version
        h5cc -show
        ```

   2. **Installation Instructions**
  
      If any check failed, run the commands below to install them:
 
        - Ubuntu/Debian
        ```bash
        sudo apt update	
        sudo apt install git python3 python3-venv	
        sudo apt install libhdf5-dev
        ```

        - macOS
        ```bash
        brew install python
        brew install git
        brew install hdf5
        ```

---

### Installation / Deinstallation

To get started with "STRIKE A POSE!", follow these steps:

1. **Clone this Git repository** to your local machine and navigate into the project directory:

   ```bash
   git clone https://github.com/alx-sch/STRIKE_A_POSE_Body_Pose_Classification_Game.git
   cd STRIKE_A_POSE_Body_Pose_Classification_Game
   ```

2. **Create and activate a virtual environment** for better isolation of dependencies:

    ```bash
    python3 -m venv strike_a_pose_env
    source strike_a_pose_env/bin/activate
    ```

3. **Install the game-specific requirements:**
    ```bash
    pip install --upgrade pip
    pip install --no-cache-dir -r requirements.txt
    ```

4.  **Run the Game!**

    Start the game by specifying the number of rounds and the time between poses (in seconds). For controls, check the [How to Play](#how-to-play) section below.
    
    ```bash
    python play.py <NUMBER_OF_ROUNDS> <SECONDS_BETWEEN_POSES>
    ```

    **Example:** `python play.py 10 5`      
    **Note:** This might take 2–3 minutes when executing for the first time.

**Post-Game Commands**

5.  **Exit the environment**
      
    When you are done playing, but want to keep the game installed for later:
    
    ```bash
    deactivate
    ```

6.  **Re-run the Game**
       
    To play again later (after running step 5), navigate back to the game directory and re-activate the environment:   
    
    ```bash
    source strike_a_pose_env/bin/activate
    python play.py <NUMBER_OF_ROUNDS> <SECONDS_BETWEEN_POSES>
    ```

7.  **Deinstallation**
 
    To completely remove the game, its environment, and free up disk space, run this command block while you are inside the game directory (or simply delete the folder `STRIKE_A_POSE_Body_Pose_Classification_Game`):
        
    ```bash
    deactivate 2>/dev/null
    cd ..
    rm -rf STRIKE_A_POSE_Body_Pose_Classification_Game
    ``` 

---

### How to Play
To play "STRIKE A POSE!", follow these steps:

1. Open a terminal and ensure your virtual environment is active (Step 6 above).

2. Start the game by specifying the number of rounds and the time between poses. For example: `python play.py 10 5`.

3. A window with a video feed will appear. Adjust your position and camera angle to fit the **green square**.
   
4. Controls:
   - Press the `Space` key to start the countdown.
   - Press `r` to restart the game or `q` to quit the game

---

### Make it Yours!

Adjust the game to your needs! 💪     
Please take a look at the documentation in `collect_data.py`, `train_model.ipynb`, and `play.py` for details.
- Collect training data of poses of your choice with **`collect_data.py`**.
- Train a new model to detect these new poses and evaluate the model's performance using **`train_model.ipynb`**. You are encouraged to explore and experiment with different model architectures.
- Adjust the model used, poses, and respective sound files in **`play.py`** to start your new Pose Game!

#### Example: Adding New Poses ("Dab" and "Jump")

1. **Collect Data for New Poses (`collect_data.py`)**      
    Since the data for the existing poses is already collected, you only need to run the data collection script for the new poses (dab and jump). The new data will be appended to the existing dataset. First, adjust the data collection script to define and record the new poses.

   - **Edit `collect_data.py`**      
     Open `collect_data.py` and modify the `POSES` list to include only the new poses you need to record.
     
     ```python
     POSES = ["dab", "jump"]
     ```

   - **Run the Collection Script**      
     Run the updated script and perform the **Dab** and **Jump** poses when prompted.
     
     ```python
     python collect_data.py
     ```

2. **Train the New Model (`train_model.ipynb`)**        
    Now you update the training script to recognize the full set of your final poses and retrain the model.

     -  **Update the Pose List in the Notebook**  
     Open `train_model.ipynb`. In the section that defines the model labels, ensure the list includes ALL seven final poses (old and new):     
     
          ```python
          POSES_ALL = ["stand", "squat", "X", "empty", "other", "dab", "jump"]
        
          # The create_label_mapping function will sort them and assign codes.
          # Example final LABEL_MAP (due to alphabetical sorting):
          # {'X': 0, 'dab': 1, 'empty': 2, 'jump': 3, 'other': 4, 'squat': 5, 'stand': 6}
          ```

   - **Execute Training**       
     Execute every cell in the notebook sequentially (`Run All`). The model will load all collected data, train on the combined 7 classes, and save the new model file.
     
        ```python
        python collect_data.py
        ```
3. **Integrate and Play (`play.py`)**     
    Finally, update the game script to use the exact 7-class structure defined by the trained model.

   -  **Edit `play.py`**  
     Open `play.py` and modify the `LABEL_MAP` dictionary in the `PARAMETERS` section to reflect the model's new, complete, alphabetically sorted structure:   
     
         ```python
         # NOTE: This MUST match the full set of poses and the ALPHABETICAL ordering used during model training!
         LABEL_MAP = {"X": 0, "Dab": 1, "Hide": 2, "Jump": 3, "Pose": 4, "Squat": 5, "Stand": 6}
         ```

    -  **Run the Game**    
     You can now run the game using your new model and seven-pose set:
     
          ```python
          python play.py 10 5
          ```

---

### Audio Credits
- Background music is sampled by [KevWest: Funky Disco Beat](https://www.looperman.com/loops/detail/332124/funky-disco-beat-free-123bpm-disco-drum-loop).
- Sound effects are downloaded from [Pixabay](https://pixabay.com/) (CC0 License).
- Commands and in-game speech are generated using the Python library gTTS (Google Text-to-Speech).

---

### Acknowledgments

I would like to thank Daniel Bärenbräuer for his outstanding project ["Live Sign Language Translator"](https://github.com/d-db/SPICED_Final_Project_Live_Sign_Language_Translator__LSTM_Neural_Network),  which served as a valuable source of inspiration for "STRIKE A POSE!".
