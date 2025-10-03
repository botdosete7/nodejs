const TelegramBot = require('node-telegram-bot-api');

// Pega o token da variável de ambiente do Railway
const token = process.env.TELEGRAM_TOKEN;
const bot = new TelegramBot(token, { polling: true });

// Comando /start
bot.onText(/\/start/, (msg) => {
  const chatId = msg.chat.id;
  bot.sendMessage(chatId, "👋 Olá! Eu sou seu bot do Telegram rodando no Railway.\n\nDigite /help para ver os comandos disponíveis.");
});

// Comando /help
bot.onText(/\/help/, (msg) => {
  const chatId = msg.chat.id;
  bot.sendMessage(chatId, "📌 Comandos disponíveis:\n\n/start - Inicia a conversa\n/help - Mostra os comandos\n/echo <texto> - Repete sua mensagem\n/info - Mostra informações do usuário");
});

// Comando /echo
bot.onText(/\/echo (.+)/, (msg, match) => {
  const chatId = msg.chat.id;
  const resp = match[1]; // texto após o comando
  bot.sendMessage(chatId, `🔁 ${resp}`);
});

// Comando /info
bot.onText(/\/info/, (msg) => {
  const chatId = msg.chat.id;
  const user = msg.from;
  bot.sendMessage(chatId, `ℹ️ Seu nome: ${user.first_name}\nID: ${user.id}\nUsername: @${user.username || "não definido"}`);
});

// Resposta para qualquer outra mensagem
bot.on('message', (msg) => {
  const chatId = msg.chat.id;
  const text = msg.text;

  // Evita responder os comandos de novo
  if (text.startsWith('/')) return;

  bot.sendMessage(chatId, `🤖 Você disse: ${text}`);
});

console.log("✅ Bot do Telegram rodando no Railway!");
