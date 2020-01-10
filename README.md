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
#### 
```
cat << EOF
The current working directory is: $PWD
You are logged in as: $(whoami)
EOF
```
#### Assign the output of command to variable
```
VAR2=$(uname -a)
```
#### Local and remote variable assignements
```
ssh -T $HOST <<'EOSSH'
VAR1=`pwd`
echo $VAR1

VAR2=$(uname -a)
echo $VAR2

EOSSH
```
#### Mixing the local and remote variables. 
```
LOCAL_VAR_1="LOCAL_VAR_1_VALUE"

ssh -T $HOST << EOSSH
echo $LOCAL_VAR_1

REMOTE_VAR_1=`pwd`
echo \$REMOTE_VAR_1

EOSSH
```
