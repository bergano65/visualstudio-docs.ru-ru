---
title: "Поддержка NGen в VSIX v3 | Документы Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 433ff9555ce4a3e896aca1143ee649217f80dc7f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ngen-support-in-vsix-v3"></a>Поддержка NGen в VSIX v3

С Visual Studio 2017 г. и новый v3 VSIX расширения (версия 3) манифеста формат расширения дают возможность разработчикам «ngen» их сборок во время установки.

Ниже приведен фрагмент кода MSDN, назначение какие «ngen».

>Генератор образов в машинном коде (Ngen.exe) — это средство повышения быстродействия управляемых приложений. Программа Ngen.exe создает образы в машинном коде, представляющие собой файлы, содержащие компилированный, специфический для процессора машинный код, и устанавливает их в кэш образов в машинном коде на локальном компьютере. Среда выполнения может использовать образы в машинном коде, находящиеся в кэше, вместо использования JIT-компилятора для компиляции исходной сборки.
>
>из [Ngen.exe (генератор образов в машинном коде)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Чтобы «ngen» сборку VSIX необходимо установить «для каждого экземпляра на компьютере». Эту возможность можно включить, установив флажок «все пользователи» в конструкторе extension.vsixmanifest:

![Проверьте все пользователи](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Включение Ngen

Чтобы включить ngen для сборки, можно использовать **свойства** в Visual Studio.

Существует 4 свойства, которые могут быть установлены:

1. **NGen** (логическое значение) — значение true, если установщик Visual Studio будет «ngen» сборки.
2. **NGen приложения** (строку) также предоставляет возможность использовать файл app.config приложения, чтобы разрешить зависимости сборки Ngen. Это значение должно быть присвоено приложения app.config, которого вы хотите использовать (относительно каталога установки Visual Studio).
3. **Архитектура NGen** (enum) — архитектура скомпилировать в собственном коде сборки. Параметрами являются:. B не указан. X86 c. X64 d. Все
4. **Приоритет NGen** (целое число от 1 до 3) — уровень приоритета Ngen задокументирован по [уровни приоритета Ngen.exe](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Здесь рассматривается **свойства** окна в действии:

![NGen в свойствах](media/ngen-in-properties.png)

Это будет добавьте ссылку на проект в проект VSIX CSPROJ-файл метаданных:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**Примечание:** CSPROJ-файл можно редактировать напрямую, если вы предпочитаете.

## <a name="extra-information"></a>Дополнительные сведения

Свойство конструктора изменения применяются не только ссылки на проект; можно задать метаданные Ngen для элементов в проекте, а также (используя те же методы, описанные выше) столько, сколько их сборок .NET.