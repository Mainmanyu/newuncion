# newuncion
 import discord

from discord.ext import commands

import os, random

import requests

intents = discord.Intents.default()

intents.message_content = True

 

bot = commands.Bot(command_prefix='$', intents=intents) # $mem  

 

@bot.event

async def on_ready():
    print(f'We have logged in as {bot.user}')

    

@bot.command()

async def mem(ctx):

    img_name = random.choice(os.listdir('images'))

    with open(f'images/{img_name}', 'rb') as f:

        # В переменную кладем файл, который преобразуется в файл библиотеки Discord!

        picture = discord.File(f)

   # Можем передавать файл как параметр!

    await ctx.send(file=picture)

def get_dog_image_url():    
    url = 'https://random.dog'
    res = requests.get(url)
    data = res.json()
    return data['url']


@bot.command('dog')
async def dog(ctx):
    '''По команде duck вызывает функцию get_dog_image_url'''
    image_url = get_dog_image_url()
    await ctx.send(image_url)
    
    

bot.run('')

