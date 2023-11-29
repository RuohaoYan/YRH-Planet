# 加载模型
```python
state_dict_pretrained = torch.load('/data/yrh/muws/ti/tibert/pytorch_model.bin',map_location='cuda:0')
```
# 结构
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/bb7cfe07-042e-472e-bbed-de71270d24ba)

bert.embeddings.position_id 是一个表示输入标记在句子中位置的整数值。它是为了指示每个输入标记的相对位置而引入的。位置ID对应于输入序列中的每个位置，从 0 开始递增，用于表示不同标记的位置。  
bert.embeddings.position_embeddings.weight 是一个权重矩阵，用于学习位置编码的向量表示。它的维度是 (max_position_embeddings, hidden_size)，其中 max_position_embeddings 是BERT模型中的最大位置编码数，而 hidden_size 是隐藏层的大小。位置编码矩阵中的每一行对应于一个位置，它包含了该位置的向量表示。  
当bert.embeddings.position_id值为0时，则取bert.embeddings.position_embeddings.weight第0个权重
```python
print(state_dict_pretrained['bert.embeddings.position_ids'].size())  
print(state_dict_pretrained['bert.embeddings.word_embeddings.weight'].size())  
print(state_dict_pretrained['bert.embeddings.position_embeddings.weight'].size())  
print(state_dict_pretrained['bert.embeddings.token_type_embeddings.weight'].size())  
print(state_dict_pretrained['bert.embeddings.LayerNorm.weight'].size())  
print(state_dict_pretrained['bert.embeddings.LayerNorm.bias'].size())  
torch.Size([1, 512])  
torch.Size([30005, 768])  
torch.Size([512, 768])  
torch.Size([2, 768])  
torch.Size([768])  
torch.Size([768])
```
单个句子或段落：如果输入只包含一个句子或段落，那么通常会使用 bert.embeddings.token_type_embeddings.weight[0] 作为类型编码向量。这是因为在这种情况下，只有一个句子或段落需要被编码，而不需要区分不同的句子或段落。两个句子或段落：如果输入包含两个句子或段落，通常会使用 bert.embeddings.token_type_embeddings.weight[0] 和 bert.embeddings.token_type_embeddings.weight[1] 来区分它们。例如，在句子对分类任务中，输入序列可以是两个句子的组合，其中第一个句子使用 bert.embeddings.token_type_embeddings.weight[0] 进行编码，第二个句子使用 bert.embeddings.token_type_embeddings.weight[1] 进行编码。


![image](https://github.com/YRH0/YRH-Planet/assets/74707759/25a19691-f11e-46a6-9581-99caf328fed3)
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/a74fd0be-e2e5-45e3-8b89-622db2d2e7cd)
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/043f1ddd-9444-4e4d-b8eb-c7bc914a5cc0)
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/cf51b12b-9e4d-43ea-bf19-38a6c5acca07)
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/3a960401-fe97-41f1-9da8-da714c370830)




