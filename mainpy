from pyrogram import Client
import asyncio
from apscheduler.schedulers.asyncio import AsyncIOScheduler
from flask import Flask
from threading import Thread

# Telegram API ma'lumotlari
API_ID = 26826024
API_HASH = "58542e0c4c4d55b2aec530947649dc60"

# Guruhlar ID ro'yxati (1754056696539 o‘chirildi)
TARGET_CHATS = [
    -1001572916927, -1001534022169, -1002370663987, -1001849762861, -1001701312606,
    -1001646703705, -1001481313340, -1001476894507, -1001701498277, -1001877275873,
    -1001688389092, -1001707543600, -1001286020404, -1001514454110, -1001275644453,
    -1001442401854, -1002115430433, -1001219604726, -1001187348763, -1001535487533,
    -1002004633205, -1001975701510, -1001769832356, -1001839877636, -1001739672977,
    -1001466930537, -1001243311912, -1001552331014, -1001577594234, -1001613027878,
    -1001360711627, -1001888298954, -1001531247478, -1001610934871
]

# Reklama matni
AD_TEXT = """🇪🇺Ассаломалекум 🇪🇺
⁠⁠⁠⁠⁠Всем привет👋
У нас есть всё необходимое
Почта ✉️ 
Доставка 📦

Свяжитесь с нами
Почта ✉️ 
Доставка 📦

Под заказ любой ₽$€

Телеграм +79630871841
WhatsApp +79630871841
WhatsApp +79630871841 ☎️
"""

# Userbot sessiya
app = Client("userbot_session", api_id=API_ID, api_hash=API_HASH)
scheduler = AsyncIOScheduler()

async def send_ads():
    for chat_id in TARGET_CHATS:
        try:
            await app.send_message(chat_id, AD_TEXT)
            print(f"✅ Xabar yuborildi: {chat_id}")
        except Exception as e:
            print(f"❌ Xato: {e}")

async def main():
    await app.start()
    scheduler.add_job(send_ads, "interval", hours=4)
    scheduler.start()
    print("✅ Userbot ishga tushdi")
    await asyncio.Event().wait()

flask_app = Flask('')

@flask_app.route('/')
def home():
    return "Userbot ishlayapti!"

def run():
    flask_app.run(host='0.0.0.0', port=8080)

def keep_alive():
    t = Thread(target=run)
    t.start()

if name == "__main__":
    keep_alive()
    asyncio.run(main())
