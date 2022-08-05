from PIL import Image, ImageDraw, ImageFont
import discord
from discord.ext import commands
from os import remove as os

intents = discord.Intents().default()
intents.members = True

client = commands.Bot(command_prefix=".", intents=intents)

@client.event
async def on_member_join(member):
    await member.avatar_url_as(static_format="png", size=1024).save("Avatar.png")
    avatar = Image.open("Avatar.png")
    if avatar.size[0] == 1024:
        pass
    else:
        avatar.resize((1024, 1024)).save("avatar.png")
        avatar = Image.open("avatar.png")

    white = Image.open("white.png")
    white.paste(avatar, (1400, 0))
    white.save("Avatar.png")

    avatar = Image.open("Avatar.png")
    background = Image.open("Background.jpg")


    mask = Image.new("L", (avatar.size), 0)
    draw = ImageDraw.Draw(mask)
    draw.ellipse([1400, 0, 2424, 1024], fill=255)
    im = Image.composite(avatar, background, mask)
    draw = ImageDraw.Draw(im)
    font = ImageFont.truetype("GothamMedium.ttf", 150)
    username = "hiere"
    

    

    draw.text((900, 1175), f"NEW MEMBER: {username}#{member.discriminator}", (244, 244, 244), font=font)
    im.resize((1920, 1080)).save("welcome.png")
    welcome = member.guild.get_channel(911934997424914443)
    await welcome.send(content=f"Hey {member.mention}, welcome to the server {member.guild.name}!\nWe hope you have some great time on the server.",file=discord.File("welcome.png"))

    os("welcome.png")
    os("avatar.png")














client.run("OTg3Nzk0MTEwMzA1OTQ3NjY4.GjHpJv.yTtfcFEAI2TvtilLYsbnHKg7_UWHymzDc4Og6k")
