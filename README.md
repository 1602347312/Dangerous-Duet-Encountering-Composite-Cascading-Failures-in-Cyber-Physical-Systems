# technical-report
Since the cyber-physical system can be modeled as an interdependent network, which is a graph, we choose GNN (implemented by GCNConv layers using the torch_geometric library) to extract the meaningful implicit or explicit features of the graph, and the generated embedding is then used as the input of the downstream task. In our work, the downstream task is to predict the time-varing results of the cascading failure, which is a time series prediction task, and thus we naturally choose RNN (LSTM in our experiments) to predict the cascading series.

## Experiment details:
### Environment: 
Intel Xeon Gold 6226R CPU, RTX 3090, 64G RAM

### Dataset: 
We use the cascading failure simulator mentioned in the paper to generate dataset. Specifically, we first generate different networks, and then record the average results (200 runs) of each failure scenario. Finally we collect about 120,000 pieces of data, and we split them into train, validation and test dataset in an 8:1:1 ratio.

### Hyperparameter: 
lr: 0.001, batch_size: 32, epoch: 50

### GNN:  
layers: 2, input_dim: 3, hidden_dim: 16

### RNN: 
layers: 2, input_dim: 16, hidden_dim: 32, seq_length: 40, output_dim: 1
