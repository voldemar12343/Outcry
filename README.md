	import telebot
	from telebot import types

	bot = telebot.TeleBot('1502913309:AAEa0888pI386oxT06OIuMQGNzJLqSyuUV4')
	keyboard1 = types.ReplyKeyboardMarkup(True)
	k1 = types.KeyboardButton('товары 👕')
	keyboard1.add(k1)

	@bot.message_handler(commands=['start'])
	def welkome(message):
    	bot.send_photo(message.chat.id, open('C:\my documents\outrcry.jpg', 'rb'))
    	bot.send_message(message.chat.id, 'Привет, {0.first_name} {0.last_name}!\nЯ - <b>{1.first_name}</b>, интернет-магазина одежды.\nМолодой экспрессивный проект. Выражает собой собранные эмоции художника, в которых, каждый, может увидеть свое отражение.\nМой магазин в других соц.сетях🔥\n📌Группа Вк https://vk.com/outcry_999\n📌inst https://www.instagram.com/outcry_999/?hl=ru\nДоставка по почте России.'.format(message.from_user, bot.get_me()),
        	parse_mode='html', reply_markup=keyboard1)

	@bot.message_handler(content_types=['text'])
	def send_text(message):
    	if message.text.lower() == 'товары 👕':
        	keyboard2 = types.InlineKeyboardMarkup()
        	btn1 = types.InlineKeyboardButton(text='худи "stagnation"', callback_data='1')
        	btn2 = types.InlineKeyboardButton(text='футболка "T-Shirt"', callback_data='2')
        	btn3 = types.InlineKeyboardButton(text='свитшот "freshness"', callback_data='3')
        	btn4 = types.InlineKeyboardButton(text='худи "DEAD END"', callback_data='4')
        	btn5 = types.InlineKeyboardButton(text='футболка "BURNING HEAD"', callback_data='5')
        	btn6 = types.InlineKeyboardButton(text='свитшот  "Hell Boy"', callback_data='6')
        	keyboard2.add(btn1, btn2, btn3, btn4, btn5, btn6)
        	bot.send_message(message.chat.id, text="Выберете товар.", reply_markup=keyboard2)

	@bot.callback_query_handler(func=lambda call: True)
	def callback_inline(call):
    	try:
        	if call.message:
            	if call.data == '1':
                	bot.send_message(call.message.chat.id, '"stagnation"\n1 800 ₽\nМатериал - хлопок 70%, полиэстер 22%, 8% лайкра\nРазмер - XL\nРисунок нанесен акрилом и закреплен\nКУПИТЬ👇\nhttps://getmoneysite.ru/s/stagnation-EixS')
                	bot.send_photo(call.message.chat.id, open('C:\my documents\stagnation.jpg', 'rb'))
            	if call.data == '2':
                	bot.send_message(call.message.chat.id, '"T-Shirt"\n650 ₽\nМатериал - хлопок\nРазмер - XL\nРисунок нанесен акрилом и закреплен\nКУПИТЬ👇\nhttps://getmoneysite.ru/s/t_shirt-A03D')
                	bot.send_photo(call.message.chat.id, open('C:\my documents\T-Shirt.jpg', 'rb'))
            	if call.data == '3':
                	bot.send_message(call.message.chat.id, '"freshness"\n1 650 ₽\nМатериал - хлопок\nРазмер - L\nПатчворкинг\nКУПИТЬ👇\nhttps://getmoneysite.ru/s/freshness-egMR')
                	bot.send_photo(call.message.chat.id, open('C:\my documents\zreshness.jpg', 'rb'))
            	if call.data == '4':
                	keyboard3 = types.InlineKeyboardMarkup()
                	btn = types.InlineKeyboardButton(text='➡', callback_data='a')
                	keyboard3.add(btn)
                	bot.send_message(call.message.chat.id, '"DEAD END"\n2 100 ₽\nМатериал - хлопок\nРазмер - XL\nРисунок нанесен акрилом и закреплен\nКУПИТЬ👇\nhttps://getmoneysite.ru/s/dead_end-utuL')
                	bot.send_photo(call.message.chat.id, open('C:\my documents\DEAD END1.jpg', 'rb'), reply_markup=keyboard3)
            	if call.data == '5':
                	bot.send_message(call.message.chat.id, '"BURNING HEAD"\n500 ₽\nМатериал - хлопок\nРазмер - XL\nРисунок нанесен акрилом и закреплен\nКУПИТЬ👇\nhttps://getmoneysite.ru/s/burning_head-4O50')
                	bot.send_photo(call.message.chat.id, open('C:\my documents\BURNING HEAD.jpg', 'rb'))
            	if call.data == '6':
                	keyboard4 = types.InlineKeyboardMarkup()
                	btn = types.InlineKeyboardButton(text='➡', callback_data='b')
                	keyboard4.add(btn)
                	bot.send_message(call.message.chat.id, '"Hell Boy"\n690 ₽\nМатериал - хлопок\nРазмер - 2XL\nРисунок нанесен акрилом и закреплен\nКУПИТЬ👇\nhttps://getmoneysite.ru/s/hell_boy-tyYB')
                	bot.send_photo(call.message.chat.id, open('C:\my documents\Hell Boy1.jpg', 'rb'), reply_markup=keyboard4)

        	if call.message:
            	if call.data == 'a':
                	bot.send_photo(call.message.chat.id, open('C:\my documents\DEAD END2.jpg', 'rb'))
        	if call.message:
            	if call.data == 'b':
                	bot.send_photo(call.message.chat.id, open('C:\my documents\Hell Boy2.jpg', 'rb'))

    	except Exception as e:
        	print(repr(e))

	bot.polling(none_stop=True)
