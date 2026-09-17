# telegram-bot
import telebot

TOKEN = "8937057272:AAFTeFvuX-iAHIC34suPinFpRxNYNBcMzng"
bot = telebot.TeleBot(TOKEN)

# Сюда вставь числовой ID этой девочки (без кавычек, это просто число)
ADMIN_ID = 7383625331  # <--- Замени на её настоящий ID

@bot.message_handler(commands=['start'])
def send_welcome(message):
    text = (
        "Здравствуйте!🍙\n\n"
        "🪦Напишите Ваш вопрос, и мы ответим Вам в ближайшее время! 🌟\n\n"
        "Ссылка на инфо канал🌟🌟\n\n"
        "https://t.me/DISPERSION_info"
    )
    bot.send_message(message.chat.id, text)

# Пример секретной команды только для неё
@bot.message_handler(commands=['admin'])
def admin_panel(message):
    # Проверяем, совпадает ли ID написавшего с ID девочки
    if message.from_user.id == ADMIN_ID:
        bot.send_message(message.chat.id, "Привет! Вот тебе полный доступ к управлению ботом 🌟")
        # Здесь можно прописать любые секретные функции
    else:
        bot.send_message(message.chat.id, "У тебя нет доступа к этой команде!")

if __name__ == '__main__':
    print("Бот запущен...")
    bot.infinity_polling()
    
