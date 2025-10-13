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
    pip install  --no-cache-dir -r requirements.txt
    ```

4.  **Run the Game!**

    Start the game by specifying the number of rounds and the time between poses (in seconds). For controls, check the [How to Play](#how-to-play) section below.
    
    ```bash
    python play.py <NUMBER_OF_ROUNDS> <SECONDS_BETWEEN_POSES>
    ```

    **Example:** `python play.py 10 5`      
    **Note:** This might take 1–2 minutes when executing for the first time.

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
 
    To completely remove the game, its environment, and free up disk space, run this command block while you are inside the game directory:
        
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
Please take a look at the documentation in collect_data.py, train_model.ipynb, and play.py for details.
- Collect training data of poses of your choice with **collect_data.py**.
- Train a new model to detect these new poses and evaluate the model's performance using **train_model.ipynb**. You are encouraged to explore and experiment with different model architectures.
- Adjust the model used, poses, and respective sound files (see [Audio Credits](#audio-credits)) in **play.py** to start your new Pose Game!

---

### Audio Credits
- Background music is sampled by [KevWest: Funky Disco Beat](https://www.looperman.com/loops/detail/332124/funky-disco-beat-free-123bpm-disco-drum-loop).
- Sound effects are downloaded from [Pixabay](https://pixabay.com/) (CC0 License).
- Commands and in-game speech are generated using the Python library gTTS (Google Text-to-Speech).

---

### Acknowledgments

I would like to thank Daniel Bärenbräuer for his outstanding project ["Live Sign Language Translator"](https://github.com/d-db/SPICED_Final_Project_Live_Sign_Language_Translator__LSTM_Neural_Network),  which served as a valuable source of inspiration for "STRIKE A POSE!".
