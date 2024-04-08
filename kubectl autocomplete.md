# Kubectl autocomplete
* echo "source <(kubectl completion bash)" >> ~/.bashrc # add autocomplete permanently to your bash shell.
* echo "alias k=kubectl" >> ~/.bashrc 
* echo "complete -o default -F __start_kubectl k" >> ~/.bashrc
* source ~/.bashrc
