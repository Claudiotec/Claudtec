@echo off
REM ==== CONFIGURAÇÕES ====
set REPO_URL=https://https://github.com/Claudiotec/claudtectecnologia
set MENSAGEM=Atualização automática

REM ==== IR PARA A PASTA DO PROJETO ====
cd /d "%~dp0"

REM ==== INICIALIZAR GIT SE PRECISAR ====
git init

REM ==== ADICIONAR ORIGIN SE NÃO EXISTIR ====
git remote -v | find "origin" >nul
if errorlevel 1 (
    git remote add origin %REPO_URL%
)

REM ==== ADICIONAR ARQUIVOS E COMMIT ====
git add .
git commit -m "%MENSAGEM%"

REM ==== DEFINIR BRANCH E ENVIAR ====
git branch -M main
git push -u origin main

pause
