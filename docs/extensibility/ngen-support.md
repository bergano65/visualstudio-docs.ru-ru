---
title: "Поддержка NGen в VSIX v3 | Документы Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 46b6f4d13b4c1938797dbe6cf6023e3c8c42d1ed
ms.lasthandoff: 03/07/2017

---
# <a name="ngen-support-in-vsix-v3"></a>Поддержка NGen в VSIX v3

С помощью Visual Studio 2017 г. и новый v3 VSIX расширение (версии 3) манифеста формат расширения разработчики могут «ngen» их сборки во время установки.

Ниже приведен отрывок из MSDN с объяснением какие» ngen».

>Генератор образов в машинном коде (Ngen.exe) — это средство повышения быстродействия управляемых приложений. Программа Ngen.exe создает образы в машинном коде, представляющие собой файлы, содержащие компилированный, специфический для процессора машинный код, и устанавливает их в кэш образов в машинном коде на локальном компьютере. Среда выполнения может использовать образы в машинном коде, находящиеся в кэше, вместо использования JIT-компилятора для компиляции исходной сборки.
>
>из [Ngen.exe (генератор образов в машинном коде)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Чтобы «ngen» сборка VSIX должен устанавливаться «каждого экземпляра каждого компьютера». Эту возможность можно включить, установив флажок «все пользователи» в конструкторе extension.vsixmanifest:

![Проверка всех пользователей](~/extensibility/media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Как включить Ngen

Чтобы включить ngen для сборки, можно использовать **свойства** в Visual Studio.

Существует 4 свойства, которые могут быть установлены:

1. **NGen** (Boolean) — значение true, если установщик Visual Studio будет «ngen» сборку.
2. **Приложение NGen** (строковый) — Ngen также предоставляет возможность использовать файл app.config приложения для разрешения зависимостей сборки. Это значение должно быть присвоено приложения app.config, которого вы хотите использовать (относительно каталога установки Visual Studio).
3. **Архитектура NGen** (enum) — архитектура скомпилировать в собственном коде сборки. Параметрами являются:. B не указан. X86 c. X64 d. Все
4. **Приоритет NGen** (целое число от 1 до 3) – уровень приоритета Ngen описано в разделе [уровни приоритета Ngen.exe](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Здесь рассматривается **свойства** окна в действии:

![NGen в свойствах](~/extensibility/media/ngen-in-properties.png)

Ссылка на проект в проект VSIX CSPROJ-файл будет добавлен метаданных:

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

 >**Примечание:** вы можете изменить CSPROJ-файл напрямую, если вы предпочитаете.

## <a name="extra-information"></a>Дополнительные сведения

Применить изменения свойств конструктора больше, чем просто ссылки проекта; можно задать метаданные Ngen элементов внутри проекта, а также (используя те же методы, описанные выше) при условии их сборок .NET.
