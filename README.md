import discord

from discord.ext import commands

import os, random

intents = discord.Intents.default()

intents.message_content = True

bot = commands.Bot(command_prefix='!', intents=intents) # !mem

@bot.event
async def on_ready():
    print(f'We have logged in as {bot.user}')


@bot.command()
async def hello(ctx):
    await ctx.send(f'Приветствую тебя на моем дискорд канале для того, чтобы помочь планете.!')
    await ctx.send(f'Тебе необходимо сделать 3 следующие вещи для того чтобы понизить количество выбрасываемых продуктов')
    await ctx.send(f'Для инструкции введи !help')

@bot.command()
async def help(ctx):
    await ctx.send(f'Отправь в чат !One/!Two/!Three для получение 3 советов ')
    await ctx.send(f'Отправь в чат !Bio для получение магазина биопродуктов')
    await ctx.send(f'Отправь в чат !ecomem для получение мема про экологию')

@bot.command()
async def Bio(ctx):
    await ctx.send(f'Ссылка на биомагазин: http://www.rebio.ru/')

@bot.command()
async def One(ctx):
    await ctx.send(f'Тебе необходимо понизить количество потребляемых продуктов откажись от употребления ненужных тебеэто поможет не только твоему кошельку но и планете')  

@bot.command()
async def Two(ctx):
    await ctx.send(f'Повторно используя вещи которые тебе не нужны сейчас сделай из них например рассаду')

@bot.command()
async def Three(ctx):
    await ctx.send(f'И наконец 3 для самых богатых для того чтобы минимизировать урон планете своим мусорам он должен быть биоразлагаемым покупай продукцию в биоразлагаемых упаковках да это дорого но не так дорого как поплатятся все человечество через некоторое время ты можешь также заказывать подобную продукцию через маркетплейсы')


bot.run('')


