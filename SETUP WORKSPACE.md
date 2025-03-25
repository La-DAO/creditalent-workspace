
## Clone repo
```warp-runnable-command
git clone git@github.com:La-DAO/creditalent-workspace.git


```
## Only First time Install \- Scaffold\-ETH 2 
```warp-runnable-command
npx create-eth@latest
```
Setup step
- [x] Put Name\: creditalent\-workspace
- [x] Select\: foundry

```warp-runnable-command
  cd creditalent-workspace    	
```
Start the local development node
```warp-runnable-command

    	yarn chain

```
    	In a new terminal window\, deploy your contracts
```warp-runnable-command
    	yarn deploy

```
  	In a new terminal window\, start the frontend
  	yarn start