# Llama 2 7B ModelBox on SambaNova DataScale SN30

1. Create a `llama7b` folder in your home repo, and copy the following two bash scripts `/projects/aitestbed_tutorial/llama7b_modelbox/7B_modelbox_fine_tuning_setup.sh` and `/projects/aitestbed_tutorial/llama7b_modelbox/7B_modelbox_fine_tuning_run.sh` to it. For example:

   ```bash
   cd $HOME
   mkdir llama7b
   cd llama7b
   cp /projects/aitestbed_tutorial/llama7b_modelbox/*.sh ./
   ```

2. Open the `7B_modelbox_fine_tuning_run.sh` file, and set the number of train steps. By default, it is set to 10, but you can change it. For example:

   ```bash
   export STEPS_THIS_RUN=10
   ```

   **Note**: make sure you set the `OUTPUT_PATH` in both `7B_modelbox_fine_tuning_setup.sh` and `7B_modelbox_fine_tuning_run.sh`, depending on where you copied the bash scripts. If you placed them under `$HOME/llama7b` as instructed in Step 1, no changes are needed. 

3. SambaNova uses SLURM for job submission and queueing. Submit the job by executing the `7B_modelbox_fine_tuning_setup.sh` bash script. For example:

   ```bash
   ./7B_modelbox_fine_tuning_setup.sh 1 llama_test
   ```

   Here, 1 refers to the number of nodes, and `llama_test` is the name of the job (you can change it).

4. You can follow the status of your job using: `squeue`.
   
5. The log file is located at `$HOME/llama7b` and is named `7B_MODELBOX_FT_1_nodes.out`:

   <details>
    <summary>Example of information in the log file </summary>
    
    ```bash
    ^M  0%|          | 1/3432 [01:17<73:27:45, 77.08s/it]2024-11-11 11:41:44,780 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - epoch:0|local_step:1|global_step:1|average_loss:7.26778|steps_per_second:0.01306|step_loss:7.26778|learning_rate:1.00e-05|eval_step:0.00000|validation_average_loss:0.00000|validation_steps_per_second:0.00000|validation_total_loss:0.00000|eval_acc:0.00000
    ^M  0%|          | 2/3432 [02:25<68:35:03, 71.98s/it]2024-11-11 11:42:53,195 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - epoch:0|local_step:2|global_step:2|average_loss:9.37396|steps_per_second:0.01462|step_loss:9.37396|learning_rate:1.00e-05|eval_step:0.00000|validation_average_loss:0.00000|validation_steps_per_second:0.00000|validation_total_loss:0.00000|eval_acc:0.00000
    ^M  0%|          | 3/3432 [03:33<67:01:22, 70.37s/it]2024-11-11 11:44:01,635 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - epoch:0|local_step:3|global_step:3|average_loss:7.11865|steps_per_second:0.01461|step_loss:7.11865|learning_rate:1.00e-05|eval_step:0.00000|validation_average_loss:0.00000|validation_steps_per_second:0.00000|validation_total_loss:0.00000|eval_acc:0.00000
    ^M  0%|          | 4/3432 [04:42<66:17:01, 69.61s/it]2024-11-11 11:45:10,085 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - epoch:0|local_step:4|global_step:4|average_loss:6.54556|steps_per_second:0.01461|step_loss:6.54556|learning_rate:1.00e-05|eval_step:0.00000|validation_average_loss:0.00000|validation_steps_per_second:0.00000|validation_total_loss:0.00000|eval_acc:0.00000
    ^M  0%|          | 5/3432 [05:51<65:57:10, 69.28s/it]2024-11-11 11:46:18,788 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - epoch:0|local_step:5|global_step:5|average_loss:7.98357|steps_per_second:0.01456|step_loss:7.98357|learning_rate:1.00e-05|eval_step:0.00000|validation_average_loss:0.00000|validation_steps_per_second:0.00000|validation_total_loss:0.00000|eval_acc:0.00000
    ^M  0%|          | 6/3432 [06:59<65:39:24, 68.99s/it]2024-11-11 11:47:27,215 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - epoch:0|local_step:6|global_step:6|average_loss:6.53741|steps_per_second:0.01462|step_loss:6.53741|learning_rate:1.00e-05|eval_step:0.00000|validation_average_loss:0.00000|validation_steps_per_second:0.00000|validation_total_loss:0.00000|eval_acc:0.00000
    ^M  0%|          | 7/3432 [08:08<65:35:58, 68.95s/it]2024-11-11 11:48:36,084 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - epoch:0|local_step:7|global_step:7|average_loss:6.58978|steps_per_second:0.01452|step_loss:6.58978|learning_rate:1.00e-05|eval_step:0.00000|validation_average_loss:0.00000|validation_steps_per_second:0.00000|validation_total_loss:0.00000|eval_acc:0.00000
    ^M  0%|          | 8/3432 [09:17<65:33:28, 68.93s/it]2024-11-11 11:49:44,960 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - epoch:0|local_step:8|global_step:8|average_loss:6.64311|steps_per_second:0.01452|step_loss:6.64311|learning_rate:1.00e-05|eval_step:0.00000|validation_average_loss:0.00000|validation_steps_per_second:0.00000|validation_total_loss:0.00000|eval_acc:0.00000
    ^M  0%|          | 9/3432 [10:25<65:26:19, 68.82s/it]2024-11-11 11:50:53,551 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - epoch:0|local_step:9|global_step:9|average_loss:5.62141|steps_per_second:0.01458|step_loss:5.62141|learning_rate:1.00e-05|eval_step:0.00000|validation_average_loss:0.00000|validation_steps_per_second:0.00000|validation_total_loss:0.00000|eval_acc:0.00000
    ^M  0%|          | 10/3432 [11:34<65:18:01, 68.70s/it]2024-11-11 11:52:01,968 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - epoch:0|local_step:10|global_step:10|average_loss:6.13464|steps_per_second:0.01462|step_loss:6.13464|learning_rate:1.00e-05|eval_step:0.00000|validation_average_loss:0.00000|validation_steps_per_second:0.00000|validation_total_loss:0.00000|eval_acc:0.00000

    ...

    2024-11-11 12:00:21,960 - apps.nlp.transformers_on_rdu.tasks.lm_tasks.gpt2_task - Process ID 2975108 - info     - {'e2e_train_time': 1194.323212146759, 'e2e_training_tokens_per_second': 4389.833461057903, 'training_tokens_per_second(exclude warmup overhead)': 7663.757280590875, 'final_loss': 2.3926801681518555}

    ```

    </details>

  6. Once the job is completed, you can see the accuracy metrics and checkpoint(s) (if enabled) at `/data/scratch/$USER/7B_MODELBOX_FT_1_nodes` 
