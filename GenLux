from discord.ext import commands
import discord
import asyncio
import requests

client = commands.Bot(command_prefix='pls')

@client.command()
@commands.has_role("DEVELOPER")
async def generate(ctx, user: discord.User):
    
    disc = user.id
    
    url = requests.get(f"https://luxterymarkfunction.000webhostapp.com/generate.php?disc={disc}")
    
    generate = url.text
    
    if generate == 'User Already Has A Key!':
        message = (f"**{user}** Already Has A Key!")
        embedVar = discord.Embed(title=message, color=0xFF0000)
        await ctx.reply(embed=embedVar)
    else:
        message = (f"Token Generated! **{user}**, Check Your DM's!")
        embedVar = discord.Embed(title=message, color=0x00ff00)
        await ctx.reply(embed=embedVar)
        await user.send(f"**Here's Your Token!** ```\n{generate}```")
        
        
@client.command()
@commands.has_role("Owner")
async def delete(ctx, user: discord.User):
    
    disc = user.id
    
    url = requests.get(f"https://luxterymarkfunction.000webhostapp.com/delete.php?disc={disc}")
    
    generate = url.text
    
    if generate == 'User Not Found':
        message = (f"**{user}** Is Not Listed In DB!")
        embedVar = discord.Embed(title=message, color=0xFF0000)
    else:
        message = (f"**{user}**'s Token Has Ben Successfully Deleted!")
        embedVar = discord.Embed(title=message, color=0x00ff00)
        

@client.event
async def on_ready():
    await client.change_presence(activity=discord.Game('Key Generator | Made By Luxtery'))

@client.event
async def on_command_error(ctx, error):
    if isinstance(error, commands.MissingRequiredArgument):
        message = (f"Please Mention A User!")
        embedVar = discord.Embed(title=message, color=0xFF0000)
        await ctx.channel.send(embed=embedVar)
    elif isinstance(error, (commands.MissingRole, commands.MissingAnyRole)):
        message = (f"You Don't Have The Permission To Use This!")
        embedVar = discord.Embed(title=message, color=0xFF0000)
        await ctx.channel.send(embed=embedVar)
    elif isinstance(error, commands.CommandNotFound):
        message = (f"Command Not Found!")
        embedVar = discord.Embed(title=message, color=0xFF0000)
        await ctx.channel.send(embed=embedVar)
       
client.run("OTMxNzg1NTQyMjEzOTg4NDIy.YeJe6Q.5rU2sVCXrddoOjFmlACCGSmbTT4")
