---
title: Многоцелевые проекты
description: В этом документе содержится обзор настройки многоцелевых проектов в Visual Studio для Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/25/2019
ms.locfileid: "75439046"
---
# <a name="projects-with-multiple-target-frameworks"></a>Проекты с несколькими целевыми платформами
В Visual Studio для Mac вы можете настроить проект Xamarin или .NET Core для запуска в любой из нескольких версий .NET Framework и на любой из нескольких системных платформ. Например, вы можете настроить запуск проекта в .NET Framework 4.6 и .NET Core 3.1. 

Дополнительные сведения о требуемых версиях .NET Framework см. в разделе [Целевые платформы](/dotnet/standard/frameworks).

> [!NOTE] 
> Этот раздел относится к Visual Studio для Mac. Сведения о Visual Studio для Windows см. в статье [Общие сведения о настройке целевой платформы](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Использование нескольких платформ

Целевые платформы указываются в файле проекта, который можно отредактировать, щелкнув правой кнопкой мыши проект и выбрав команду **Средства > Изменить файл**. Если указана одна целевая платформа, используйте элемент TargetFramework. В следующем файле проекта консольного приложения показано, как указать целевую платформу .NET Core 3.0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Используйте множественный элемент TargetFrameworks с несколькими целевыми платформами.

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Дополнительные сведения см. в разделе [Как указать целевые платформы](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Работа с кодом в многоцелевом проекте
Редактируя файл C# в проекте с несколькими целевыми платформами, вы можете указать, какую из платформ необходимо использовать для управления интерфейсом редактора (например, для отображения предупреждений, если вы используете API, не поддерживаемый этой платформой). Изменить целевую платформу можно с помощью селектора **Целевая платформа** в верхнем левом углу окна редактора.

![Использование селектора, расположенного в верхней части окна редактора, для изменения целевой платформы](media/project-multitargeting-framework-selector.png)

Иногда возникает необходимость в вызове различных API в зависимости от целевой платформы вашего приложения. С этой целью можно написать условный код для компиляции кода для конкретной платформы:

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

При написании кода в предложениях по автозаполнению IntelliSense могут отображаться предупреждения об отсутствии конкретных API для какой-либо целевой платформы, поддерживаемой вашим приложением.

![Отображаемое в IntelliSense предупреждение об отсутствии поддержки API для указанной целевой платформы. Пример текста: пространство имен System.Buffers, SharedUtils (netstandard2.0) — недоступно. Для переключения контекста можно использовать панель навигации.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>См. также

- [Общие сведения о настройке целевой платформы](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Как указать целевые платформы](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
