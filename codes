import discord
from discord.ext import commands
import requests
import json
import asyncio
from numerize import numerize
import config

Api = "123"
client = commands.Bot(command_prefix = '$')
async def status_task():

    while True:

        getir = requests.get(f"https://api.etherscan.io/api?module=gastracker&action=gasoracle&apikey={Api}").text
        getir = json.loads(getir)
        fast = getir["result"]["SafeGasPrice"]
        slow = getir["result"]["SafeGasPrice"]
        avar = getir["result"]["ProposeGasPrice"]
        await client.change_presence(activity=discord.Activity(type=discord.ActivityType.watching, name=f"🐢{slow} | 🦀{avar} | 🚀{fast}"))
       
        for guild in client.guilds:
            await guild.me.edit(nick=f"Ethereum Gas")

        await asyncio.sleep(2)

try :
    @client.event
    async def on_ready():   
        client.loop.create_task(status_task())
        print('blockland Etherbot hazir')

except :
    False

client.run(config.GAS_TOKEN)
