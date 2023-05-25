import random
import string
import telegram
from telegram.ext import CommandHandler, MessageHandler, Filters, Updater


def start(update, context):
  context.bot.send_message(chat_id=update.effective_chat.id,
                           text="Olá! Sou o bot gerador de conjuntos.")


def gerar_conjunto(update, context):
  try:
    qtd_partes = int(context.args[0])
    tam_parte = int(context.args[1])

    conjunto_gerado = gerar_conjunto(qtd_partes, tam_parte)

    resultado = "\n".join(conjunto_gerado)
    context.bot.send_message(chat_id=update.effective_chat.id, text=resultado)
  except (IndexError, ValueError):
    context.bot.send_message(
      chat_id=update.effective_chat.id,
      text="Por favor, insira a quantidade de partes e o tamanho de cada parte."
    )


def gerar_conjunto(qtd_partes, tam_parte):
  conjunto = []
  caracteres_permitidos = string.ascii_uppercase + string.digits
  for _ in range(7):
    parte = ''.join(random.choices(caracteres_permitidos, k=tam_parte))
    codigo = '-'.join([parte for _ in range(qtd_partes)])
    conjunto.append(codigo)
  return conjunto


TOKEN = '5677708055:AAGxNFXC2jWAPbbYoogC9PqiWxtZpfM6GZk'  # Substitua com o token de acesso do seu bot

updater = Updater(token=TOKEN, use_context=True)
dispatcher = updater.dispatcher

start_handler = CommandHandler('start', start)
gerar_conjunto_handler = CommandHandler('gerar_conjunto', gerar_conjunto)

dispatcher.add_handler(start_handler)
dispatcher.add_handler(gerar_conjunto_handler)

updater.start_polling()
