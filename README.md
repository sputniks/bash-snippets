# bash-snippets

### Define HOST variable to use with SSH calls
```
HOST="localhost"
```

### String variable to file
```
var="foo"
filepath=/users/me/home/text.txt
echo "$var" >> "$filepath"
```
### SSH and remotely run commands defined in the script

#### Create cmd script with first declaring string variable
```
cmd="
ls;
pwd;
hostname;
"
```
#### Then run to test it
```
eval $cmd
```
#### Write context of the variable to file
```
echo $cmd > script.sh
```
#### Run the cmd file locally
```
bash script.sh
```
#### Run the cmd file remotely with SSH
```
ssh $HOST < script.sh
```
