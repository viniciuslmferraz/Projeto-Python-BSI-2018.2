# Projeto-Python-BSI-2018.2
import sys

professores = []
alunos = []
turma = []
disciplina = []

def pede_nome():  #pede nome
  return(input("Nome: "))

def pede_cpf(): #pede CPF
  teste = input("CPF: ") # 12345678900
  if len(teste) < 11:
      teste = teste.zfill(11)
  cpf = '{}.{}.{}-{}'.format(teste[:3], teste[3:6], teste[6:9], teste[9:])
  return(cpf)

def pede_depart():   #pede departamento
  return(input("Departamento: "))

def pede_codT(): #pede código da turma
  return(input("Código da turma: "))

def pede_codD(): #pede código da disciplina
  return(input("Código da disciplina: "))

def pede_disc(): #pede a disciplina
  return(input("Disciplina: "))

def pede_periodo(): #pede o periodo
  return(input("Periodo: "))



def novo_alu(): #novo cadastro
  nome = pede_nome()
  cpf = pede_cpf()
  arquivo = open("Alunos.txt", "a", encoding = "utf-8")
  arquivo.write("%s#%s\n" % (nome, cpf))
  arquivo.close()

def novo_prof(): #novo cadastro
  global professores
  nome = pede_nome().upper().strip()
  cpf = pede_cpf().strip()
  departamento = pede_depart().strip().upper()
  arquivo = open("professores.txt", "a", encoding = "utf-8")
  arquivo.write("%s#%s#%s\n" % (nome, cpf, departamento))
  arquivo.close()
  

def nova_disc(): #novo cadastro
  nome = pede_disc()
  codigo = pede_codD()
  arquivo = open("disciplinas.txt", "a", encoding = "utf-8")
  arquivo.write("%s#%s\n" % (nome, codigo))
  arquivo.close()
  

def nova_turma(): #novo cadastro
  codturma = pede_codT()
  coddisc = pede_codD()
  periodo = pede_periodo()
  arquivo = open('Turmas.txt', 'a', encoding = 'utf-8')
  arquivo.write("%s#%s#%s\n" %(codturma, coddisc, periodo))
  arquivo.close()
  


def consulta_prof():
  global professores
  arquivo = open("professores.txt", "r")
  professores = []
  for c in arquivo.readlines():
    nome, cpf, departamento = c.strip().split("#")
    professores.append([nome, cpf, departamento])
    arquivo.close()
  p = pede_nome().upper()
  achou = False
  for i in professores:
     if i[0] == p:
        achou = True
        break  
     else:
        continue
  if achou == True:
     print("\n\n\nNome: %s\nCPF: %s\nDepartamento: %s\n\n" % (i[0], i[1], i[2]))
  else:
     print("\n\n\n ### Professor não encontrado ###\n\n\n")


def valida_faixa_inteiro(pergunta, inicio, fim):  #Validação de entrada do usuário
     while True:
         try:
               valor = int(input(pergunta))
               if inicio <= valor <= fim:
                   return(valor)
               else:
                   print("\n \nValor inválido!\nFavor digitar valores entre [%d e %d] \n \n" % (inicio, fim))
         except ValueError:
               print("Valor inválido, favor digitar entre %d e %d" % (inicio, fim))


def menu():  #menu principal
  print(""" \n\n

--------------------------------------Sistema de Controle Acadêmico Simplificado-----------------------------------------
            
                        1 - Novo cadastro (Professor)                         5 - Novo cadastro (Aluno)               
                        2 - Consulta de dados (Professor)                   6 - Consulta de dados (Aluno)                
                        3 - Atualização de dados (Professor)              7 - Atualização de dados (Aluno)                    
                        4 - Apagar dados (Professor)                          8 - Apagar dados (Aluno)                           
                                                                                              9 - Lista de turmas/aluno (Aluno)

                        10 - Novo cadastro (Disciplina)                        15 - Novo cadastro (Turma)
                        11 - Consulta de dados (Disciplina)                   16 - Consulta de dados (Turma)
                        12 - Atualização de dados (Disciplina)              17 - Atualização de dados (Turma)
                        13 - Apagar dados (Disciplina)                          18 - Apagar dados (Turma)
                        14 - Gerar ata de exercicio (Disciplina)


                                                                        0 -  SAIR  \n\n
""")
  return valida_faixa_inteiro("Escolha uma opção (0~18): ", 0, 18)


while True:                                    # while true pra cada menu

    opcao = menu()
    if opcao == 0:
      break
    elif opcao == 1:
      novo_prof()
    elif opcao == 2:
      consulta_prof()
    elif opcao == 3:
      print("ainda nao definido")
    elif opcao == 4:
      print("ainda nao definido")
    elif opcao == 5:
       novo_alu()
    elif opcao == 6:
      print("ainda nao definido")
    elif opcao == 7:
      print("ainda nao definido")
    elif opcao == 8:
      print("ainda nao definido")
    elif opcao == 9:
      print("ainda nao definido")
    elif opcao == 10:
      nova_disc()
    elif opcao == 11:
      print("ainda nao definido")
    elif opcao == 12:
      print("ainda nao definido")
    elif opcao == 13:
      print("ainda nao definido")
    elif opcao == 14:
      print("ainda nao definido")
    elif opcao == 15:
      nova_turma()
    elif opcao == 16:
      print("ainda nao definido")
    elif opcao == 17:
      print("ainda nao definido")
    elif opcao == 18:
      print(professores)
