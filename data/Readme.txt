其中social_bias_infer_data.json里面包含76994条inference sample，对应spider dataset中的train_spider.jon/dev.json的格式，
但是每条数据多了"paraphrase"和"altered_table_idx"这两个key，在使用时，
需要用新增的“paraphrase”来取代原来spider dataset中"question"来进行数据处理
（如计算question和table column names之间的linking需要改成计算paraphrase和table column names之间的linking）等其他操作。
此外，每个database的索引从原来的entry['db_id']改成了entry['db_id'] + ' ' + str(entry['altered_table_idx']。

altered_human_tables_v1.json, altered_human_tables_v2.json, altered_human_tables_v3.json这三个文件对应spider dataset中的tables.json文件，
是database tables的三个修改版本，相比原版文件只是新增了一些column names，没有新增额外的key，在使用时和原版没有区别，
在infer的过程中依次和social_bias_infer_data.json匹配使用，所以最后会得到3个版本的inference结果。