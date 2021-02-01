# SkillFactory_module_0_Mazur

import numpy as np


def game_core_v3(number):
    
    max_number = 100
    min_number = 1
    count = 1                           
    predict = np.random.randint(1,100)   
    while number != predict:
        count += 1    
        predict = (min_number + max_number)//2
        if number > predict:
            predict += 1
            min_number = predict  
        elif number < predict: 
            predict -= 1
            max_number = predict
            
    return(count)


def score_game(game_core):
    
    count_ls = []
    np.random.seed(1)             # Fix. RANDOM SEED, for reproducibility of the experiment 
    random_array = np.random.randint(1, 101, size=(1000))
    for number in random_array:
        count_ls.append(game_core(number))
    score = int(np.mean(count_ls))
    print(f"Ваш алгоритм угадывает число в среднем за {score} попыток")
    
    return(score)


score_game(game_core_v3)
