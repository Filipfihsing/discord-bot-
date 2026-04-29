main.py
import discord
import random
intents = discord.Intents.default()



intents.message_content = True

client = discord.Client(intents=intents)

@client.event
async def on_ready():
    print(f'Zalogowaliśmy się jako {client.user}')

@client.event
async def on_message(message):
    if message.author == client.user:
        return
    elif  message.content.startswith('$heh'):
        if len(message.content) > 4:
            count_heh = int(message.content[4:])
        else:
            count_heh = 5
        await message.channel.send("he" * count_heh) 
        
        
    if message.content.startswith('$cześć'):
        await message.channel.send(f'cześć o czym dzisiaj rozmawiamy?')
        
    elif message.content.startswith('$ozmainachklimatu'):
        await message.channel.send(f'To bardzo ciekawy temat. No to zaczynamy, zadawaj pytania')
        
    elif message.content.startswith('$cotozmianyklimatu'):
        await message.channel.send(f'Zmiana klimatu – zmiana stanu systemu klimatycznego, opisywana w kategoriach zmiany średniej lub zmienności jakiegoś parametru, a która utrzymuje się przez dłuższy czas. Pod pojęciem klimatu rozumie się średni stan atmosfery i oceanu w skalach od kilku lat do milionów lat, a precyzyjniej, statystyczny opis stanu systemu klimatycznego przy pomocy takich miar statystycznych jak średnia czy wariancja odnoszących się do parametrów meteorologicznych. Zmiany klimatu wynikać mogą z działania wymuszeń klimatycznych, zarówno naturalnych takich jak ilość dochodzącego promieniowania słonecznego, jak i działalności człowieka jak emisja gazów cieplarnianych, mogą być również skutkiem wewnętrznej zmienności klimatycznej. Na przełomie XX i XXI wieku termin „globalna zmiana klimatu” zaczął być używany w kontekście globalnego ocieplenia wzrostu średniej temperatury powierzchni Ziemi w odpowiedzi na wzrost koncentracji gazów cieplarnianych w atmosferze oraz towarzyszących mu zjawisk np. zmiany w występowaniu opadów, ekstremalnych zjawisk pogodowych')
        
    elif message.content.startswith('$ocieplenie'):
        await message.channel.send(f'Ocieplenie klimatu - to zjawisko gwałtownego ocieplania się planety, za które odpowiada głównie działalność człowieka, prowadząca do zwiększenia stężenia gazów cieplarnianych w atmosferze. Przez ostatnie 150 lat temperatury rosły szybciej niż kiedykolwiek wcześniej.')
        
    elif message.content.startswith('$copowodujeocieplenie'):
        await message.channel.send(f'W wyniku spalania węgla, ropy i gazu powstają dwutlenek węgla i podtlenek azotu.Wycinanie lasów (wylesianie). Drzewa pomagają regulować klimat poprzez pochłanianie CO2 z atmosfery. Kiedy są one wycinane, zmagazynowany w nich węgiel znów trafia do atmosfery, a to przyczynia się do efektu cieplarnianego.Intensywna hodowla zwierząt gospodarskich. Krowy i owce produkują duże ilości metanu podczas trawienia.Nawozy azotowe powodują emisje tlenków azotu.Fluorowane gazy cieplarniane są emitowane z urządzeń i produktów, które wykorzystują te gazy. Mają one bardzo wysoką wydajność cieplną, aż do 23 tys. razy wyższą niż CO2.')   
        
    elif message.content.startswith('$spalanie'):
        file1 = discord.File("spp.jpg", filename="spp.jpg")
        
    elif message.content.startswith('$fact'):
        await message.channel.send(random.choice(fact))
        
    elif message.content.startswith('$filmdokumentalny'):
        await message.channel.send("https://youtu.be/GcAu-rslotI")
        
    elif message.content.startswith('$skutkizmianklimatu'):
        await message.channel.send('Zmiany w środowisku naturalnym: topnienie czap polarnych, wzrost poziomu mórz i oceanów, zakwaszanie wód oraz utrata bioróżnorodności.')
        
    elif message.content.startswith('$porównanie'):
        file1 = discord.File("po1.jpg", filename="po1.jpg")
        file2 = discord.File("po2.jpg", filename="po2.jpg")
        await message.channel.send(files=[file1, file2])
        

        
client.run("BOT TOKEN")











bot.py
import discord
import random
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='$', intents=intents)




@bot.event
async def on_ready():
    print(f'Zalogowaliśmy się jako {bot.user}')

@bot.command()
async def cześć(ctx):
    await ctx.send(f'cześć o czym dzisiaj rozmawiamy?')

@bot.command()
async def ozmianachklimatu(ctx):
    await ctx.send(f'To bardzo ciekawy temat. No to zaczynamy, zadawaj pytania')

@bot.command()
async def heh(ctx, count_heh = 5):
    await ctx.send("he" * count_heh)
@bot.command()
async def cotozmianyklimatu(ctx):
    await ctx.send(f'Zmiana klimatu – zmiana stanu systemu klimatycznego, opisywana w kategoriach zmiany średniej lub zmienności jakiegoś parametru, a która utrzymuje się przez dłuższy czas. Pod pojęciem klimatu rozumie się średni stan atmosfery i oceanu w skalach od kilku lat do,milionów lat, a precyzyjniej, statystyczny opis stanu systemu klimatycznego przy pomocy takich miar statystycznych jak średnia czy wariancja odnoszących się do parametrów meteorologicznych. Zmiany klimatu wynikać mogą z działania wymuszeń klimatycznych, zarówno naturalnych takich jak ilość dochodzącegopromieniowania słonecznego, jak i działalności człowieka jak emisja gazów cieplarnianych, mogą być również skutkiem wewnętrznej zmienności klimatycznej.Na przełomie XX i XXI wieku termin „globalna zmiana klimatu” zaczął być używany w kontekście globalnego ocieplenia wzrostu średniej temperatury powierzchni Ziemi w odpowiedzi na wzrost koncentracji gazów cieplarnianych w atmosferze oraz towarzyszących mu zjawisk np. zmiany w występowaniu opadów, ekstremalnych zjawisk pogodowych.')

@bot.command()
async def ocieplenie(ctx):
    await ctx.send(f'Ocieplenie klimatu - to zjawisko gwałtownego ocieplania się planety, za które odpowiada głównie działalność człowieka, prowadząca do zwiększenia stężenia gazów cieplarnianych w atmosferze. Przez ostatnie 150 lat temperatury rosły szybciej niż kiedykolwiek wcześniej.')

@bot.command()
async def copowodujeocieplenie(ctx):
    await ctx.send(f'W wyniku spalania węgla, ropy i gazu powstają dwutlenek węgla i podtlenek azotu.Wycinanie lasów (wylesianie). Drzewa pomagają regulować klimat poprzez pochłanianie CO2 z atmosfery. Kiedy są one wycinane, zmagazynowany w nich węgiel znów trafia do atmosfery, a to przyczynia się do efektu cieplarnianego.Intensywna hodowla zwierząt gospodarskich. Krowy i owce produkują duże ilości metanu podczas trawienia.Nawozy azotowe powodują emisje tlenków azotu.Fluorowane gazy cieplarniane są emitowane z urządzeń i produktów, które wykorzystują te gazy. Mają one bardzo wysoką wydajność cieplną, aż do 23 tys. razy wyższą niż CO2.')

@bot.command()
async def fact(ctx):
    fact = ["Większość zapewne pomyślała o Afryce jako najsuchszym kontynencie. Na pewno cierpi siętam na wieczny niedobór wody jednakże żadne z tamtejszych miejsc nie szczyci się mianemtego gdzie nie padało naprawdę długo. Arica zwane miastem wiecznej wiosn jest miastemportowym w Chile. Wyliczono w tym miejscu najniższą sumę opadów na Ziemi a takżezanotowano najdłuższy okres bez opadu deszczu –14 lat i 5 miesięcy.",
            "Pytanie może się wydawać trudne, ale tak naprawdę odpowiedź jest dość oczywista. Zanimjeszcze zmobilizowało się społeczeństwo, trzeba było osób, które zauważyłyby zmianyklimatyczne i zdefiniowałyby problem. Do grona badaczy informujących o zmianachklimatycznych (i zjawiskach z nim związanych) zaliczają się: klimatolodzy, meteorolodzy,astrofizycy, geografowie i… biolodzy. Ci ostatni są w stanie obserwować wpływ zmian klimatuna różnego rodzaju żyjątka. W dalszej kolejności walki ze zmianami klimatycznymi pojawiasię jeszcze więcej zawodów: politycy, dziennikarze, inżynierowie, innowatorzy. Można więcwybrać różne ścieżki kariery, by docelowo wspomóc walkę z globalnym ociepleniem.",
            "Tak naprawdę trudno zmierzyć wpływ globalnego ocieplenia na środowisko, trudno więc też znaleźć pierwszą ofiarę. Jedną z pierwszych jest szczurzynek koralowy. To pierwszy udokumentowany ssak, który wymarł na początku XXI wieku na skutek wzrostu poziommorza. Prognozuje się, że w wyniku zmian klimatycznych co trzeci gatunek zwierząt i roślinjest lub w niedalekiej przyszłości będzie zagrożony wyginięciem.",
            "W szkole zapewne uczyliście się o różnych klimatach: równikowych, zwrotnikowych,umiarkowanych, itp. Jest to jedynie podstawowy opis. Tak naprawdę klimatów jest dość sporo,osobliwy klimat potrafią stworzyć… miasta. Miasto ze względu na sporą ilość ludzi,budynków, elementów grzewczych i spalin jest wyspą cieplną. Być może dlatego wszyscw wakacje marzą o wyjeździe na łono natury. Mieszanka ciepła i brak cyrkulacji powierzasprawiają, że temperatura w miastach jest stosunkowo wyższa. Miejski klimat styka siz różnymi problemami, między innymi ze smogiem czy z zagospodarowaniem wody opadowej.I tutaj wszyscy myślący innowacyjnie mają swoje pole do popisu. Miejskie środowiskowymaga od nas kreatywności, by rozwiązywać problemy naszego mikroklimatu. W Gdańskuna przykład stworzono ogrody deszczowe. Dzięki nim woda nie zatrzymuje się na ulicy bądźchodniku, by po chwili wyparować, ale wsiąka w grunt, wzbogacając w ten sposób ziemię.Wiąże się to również ze wzrostem roślin, a to daje szansę na więcej cienia w upalne dni. "
    ]
    await ctx.send(random.choice(fact))
    
@bot.command()
async def spalanie(ctx):
    file1 = discord.File("images/spp.jpg", filename="spp.jpg")
    embed = discord.Embed(title="Spalanie np.opon")
    embed.set_image(url="attachment://spp.jpg")
    await ctx.send(file=file1, embed=embed)
    
@bot.command()
async def porównanie(ctx):
    file1 = discord.File("images/po1.jpg", filename="po1.jpg")
    file2 = discord.File("images/po2.jpg", filename="po2.jpg")  

    embed = discord.Embed(title="Porównanie")
    embed.set_image(url="attachment://po1.jpg")

    await ctx.send(file=file1, embed=embed)
    await ctx.send(file=file2)
    
    
@bot.command()
async def skutkizmianklimatu(ctx):
    await ctx.send(f'Zmiany w środowisku naturalnym: Topnienie czap polarnych, wzrost poziomu mórz i oceanów, zakwaszanie wód oraz utrata bioróżnorodności.')
    
@bot.command()
async def filmdokumentalny(ctx, *, link=None):
    if link is None:
        await ctx.send("https://youtu.be/GcAu-rslotI")
        return

    embed = discord.Embed(
        title="Film dokumentalny",
        url=link,
        color=0xff0000
    )
    await ctx.send(embed=embed)

bot.run("BOT TOKEN")     






# żeby ten kod działał musisz zainstalować visual studio code oraz interpreter
# następnie stwóż folder  na pulpicie przenieś go do visuala utwóż pliki main.py i bot.py oraz folder images,
# pobierz zdjęcie jpg/png wpisz nazwę tam gdzie ma 'po1.jpg'
# pobierz biblioteke discord 'pip install discord' następnie jeśli masz discorda stwóż discord bota w discord developer
# następnie wklej token do 'bot.run("bot token")
# wpisz w terminal 'python bot.py', wejdź w discorda i się ciesz.






























