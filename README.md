
```shell
# create a yaml-graph container mounting the report and definition directories
docker run -it -p7474:7474 -p7687:7687 -v $(PWD)/definition:/home/ymlgraph/frameworks -v $(PWD)/report:/home/ymlgraph/report nextmetaphor/yaml-graph

# validate the definitions
yaml-graph validate -s frameworks -f frameworks/definition-format.yml  

# load into the graph
yaml-graph load -s frameworks 

# generate reports
yaml-graph report --fields report/BestPracticeByFrameworkJSON/fields.yaml --template report/BestPracticeByFrameworkJSON/template.gohtml > report/BestPracticeByFrameworkJSON/document.json
```