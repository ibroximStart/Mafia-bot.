from telegram import Update, Bot
from telegram.ext import Updater, CommandHandler, CallbackContext
import os

TOKEN = os.getenv("TOKEN")  # Keyinchalik render.comda .env fayl orqali olinadi

def start(update: Update, context: CallbackContext):
    update.message.reply_text("👋 Salom! Mafia bot ishga tushdi!")

def help_command(update: Update, context: CallbackContext):
    update.message.reply_text("Buyruqlar:\n/start - boshlash\n/help - yordam\n/mafia - o‘yin haqida")

def mafia(update: Update, context: CallbackContext):
    update.message.reply_text("Bu mafia o‘yini demo versiyasi. To‘liq versiyasi tez orada!")

def main():
    updater = Updater(token=TOKEN)
    dp = updater.dispatcher

    dp.add_handler(CommandHandler("start", start))
    dp.add_handler(CommandHandler("help", help_command))
    dp.add_handler(CommandHandler("mafia", mafia))

    updater.start_polling()
    updater.idle()

if __name__ == '__main__':
    main()