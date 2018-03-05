# Unit test sa mga smart na kontrata

Pagkatapos basahin ang nakaraang dokumento, tayo ay nagawang gumamit ng C# sa Visual Studio 2015 para maghanda ng mga smart na kontrata. Paano tayo gumawa ng mga unit test pagkatapos magsulat ng isang smart na kontrata?

## Sumulat ng mga unit test

Halimbawa, pwede kang gumawa ng sumusunod na smart na kontrata, kung saan mayroong tatlong mga parametro, ang isinasauli na halaga ay int.


```c#
using Neo.SmartContract.Framework;
using Neo.SmartContract.Framework.Services.Neo;

namespace Neo.SmartContract
{
    public class Test1: SmartContract
    {
        public static int Main (int a, int b, int c)
        {
            if (a> b)
                return a * sum (b, c);
            else
                return sum (a, b) * c;
        }

        public static int sum (int a, int b)
        {
            return a + b;
        }
    }
}
```

Pagkatapos mag-compile, buohin ang `Test1.avm` file ng kontrata. Pwede tayong gumawa ng isang unit test na proyekto at i-test ang `Test1.avm`.

Una, gumawa ng isang C# Console App (.Net Framework) na proyekto gamit ang Visual Studio, gamit ang .NET Framework 4.6.2 o mas higit pa. Pagkatapos, dumagdag ng isang reference sa `Neo.dll` at `neon.dll`.

> [!Tandaan]
> Ang dalawang mga file ay maaring makuha sa pamamagitan ng pag-compile sa [Neo](https://github.com/neo-project/neo) at [neo-vm](https://github.com/neo-project/neo-vm).

> Bilang alternatibo, pwede mo lang idagdag ang "NEO" at "Neo.VM" na mga NuGet na package sa iyong proyekto. Pwede mong gawin ito sa pamamagitan ng pag-right-click ng contract project sa Solution Explorer, pumunta sa Browse, at hanapin ang NEO at i-install ang mga kinakailangang mga package.

```c#
using System;
using System.IO;
using System.Linq;
using Neo;
using Neo.VM;
using Neo.Cryptography;

namespace ConsoleApplication1
{
    class program
    {
        static void Main(string[] args)
        {
            var engine = new ExecutionEngine(null, Crypto.Default);
            engine.LoadScript(File.ReadAllBytes(@ "C: \ ... \ Test1.avm"));

            using (ScriptBuilder sb = new ScriptBuilder())
            {
                sb.EmitPush(2); // tumutugma sa c na parametro
                sb.EmitPush(4); // tumutugma sa b na parametro
                sb.EmitPush(3); // tumutugma sa a na parametro
                engine.LoadScript(sb.ToArray());
            }

            engine.Execute(); // simulang ang eksekyusyon

            var result = engine.EvaluationStack.Peek().GetBigInteger(); // dito itakda ang isasauling halaga
            Console.WriteLine($"Execution result {result}");
            Console.ReadLine();
        }
    }
}
```

Output sa pag-compile: Resulta ng eksekyusyon ay 14, tulad ng inaasahan

> [!Tandaan]
>
> Kung matatagpo ang sumusunod na error pagkatapos mag-eksekyut:
>
> Ang tipo na “BigInteger” ay i-denifine sa isang unreferenced na assembly. Kinakailangan mong magdagdag ng reference sa assembly na “System.Numerics, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089”
>
> Pwede kang magdagdag ng isang reference sa “System.Numerics” para maresolba ang problema。

Tandaan: Kung gagamit ka ng code sa itaas para pumasa ng mga parametro, bigyang pansin ang nasa taas ng stack na naaayon sa unang parametro, pwede ring ipasa ang mga parametro gamit ang sumusunod na code para maging madali.S

```c#
using (ScriptBuilder sb = new ScriptBuilder())
{
    int[] parameter = {3, 4, 2};
    parameter.Reverse().ToList().ForEach(p => sb.EmitPush(p));
    engine.LoadScript(sb.ToArray());
}
```
Kung ang isinasauli na halaga ng smart na kontrata ay hindi int, pero ito ay bool o ibang tipo, kinakailangan mong i-set ang `engine.EvaluationStack.Peek (). GetBigInteger ()` sa ibang halaga, kagaya ng pinapakita sa Figure

[](/assets/test_1.jpg)

------

### 📖 Ang dokumento ay kasalukuyang ini-edit

Ang dokumento ay kasalukuyang ini-edit at magiging kompleto ito sa madaling panahon. Pwede mong tingnan ang ibang dokumento sa [Github wiki](https://github.com/neo-project/neo/wiki) o pumunta sa aming [opisyal na NEO website](http://www.neo.org) at tumingin dito.

Ang NEO ay isang community open source na proyekto, kung ikaw ay interesado, pwede kang tumulong sa ibang mga developer na dokumento sa pamamagitan ng paglikha ng mga Pull requests sa GitHub, ang mga dokumento para sa proyekto ay makikita sa [github.com/neo-project/docs](https://github.com/neo-project/docs), salamat sa iyong kontribusyon.
