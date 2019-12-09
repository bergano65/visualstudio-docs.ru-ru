---
title: Руководство. Миграция проектов расширяемости в Visual Studio 2015 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46b48370847cbb2cf8b171342aff9baf38c40a22
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295550"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Руководство. Миграция проектов расширяемости в Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вот как можно обновить расширение.  
  
> [!IMPORTANT]
> Если вы собираетесь поддерживать версию решения расширения для более ранней версии Visual Studio, перед обновлением необходимо создать копию. Возврат обновленной версии в предыдущее состояние может быть затруднена.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Обновление решения расширения  
  
1. Используя копию, которую необходимо обновить, откройте ее в новой версии. Вам будет рекомендовано, что обновление необратимо.  
  
2. После завершения обновления измените путь к внешней программе на новую версию devenv. exe. Щелкните правой кнопкой мыши узел проекта в **Обозреватель решений**, а затем выберите пункт **свойства**. На вкладке **Отладка** найдите текстовое поле, **запустите внешнюю программу** и измените путь к файлу devenv. exe на путь Visual Studio 2015, который должен выглядеть примерно так:  
  
     **%ProgramFiles%\Microsoft Visual Studio (Common7\IDE\devenv.exe)**  
  
3. Добавьте ссылку на Microsoft. VisualStudio. Shell. «. *. dll». (Щелкните правой кнопкой мыши узел проекта в **Обозреватель решений** и выберите **Добавить/ссылка**. Перейдите на вкладку **расширения** и проверьте **Microsoft. VisualStudio. Shell.,**  
  
4. Постройте решение. Созданные файлы развертываются в:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< имя автора\>\\< имя проекта** \>\\< версия проекта\>\\.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Обновление проекта расширения для ссылочных сборок NuGet VS SDK  
  
1. Определите эталонные сборки пакета VS SDK, необходимые для вашего проекта.  В **Обозреватель решений**разверните узел **ссылки** проекта и проверьте список ссылок проекта.  Ссылки на сборки пакета VS SDK будут иметь префикс **Microsoft. VisualStudio** в имени (например, Microsoft. VisualStudio. Shell. «~»).  
  
2. Удалите эталонные сборки пакета VS SDK из проекта, выбрав их, щелкните правой кнопкой мыши и выберите пункт **Удалить**.  
  
3. Добавьте версии NuGet для эталонных сборок пакета VS SDK.  Находясь в узле **ссылки на обозреватель решений** , откройте окно **Управление пакетами NuGet...** .  Если вы хотите узнать больше об этом диалоговом окне, см. раздел [Управление пакетами NuGet с помощью диалогового окна](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio). Эталонные сборки пакета VS SDK публикуются на [NuGet.org](https://www.nuget.org/) by [висуалстудиоекстенсибилити](https://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4. Используя **NuGet.org** в качестве **источника пакета**, найдите имя пакета NuGet, совпадающее с требуемой ссылочной сборкой (например, Microsoft. VisualStudio. Shell. г), и установите его в проекте.  NuGet может добавить несколько ссылочных сборок для удовлетворения зависимостей начальной сборки.  
  
     При желании вы можете добавить все справочные сборки пакета VS SDK одновременно, установив [мета пакет](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)SDK vs.  
  
5. Можно также переключиться на использование версии NuGet средств сборки пакета VS SDK. Этот пакет NuGet — [Microsoft. VSSDK. BuildTools.](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) после добавления в проект будут включены необходимые средства и целевые файлы, позволяющие создать проект расширения среды на компьютере без установленного пакета SDK для VS.  
  
> [!NOTE]
> Не требуется обновлять существующие проекты расширения для использования ссылочных сборок и средств NuGet.  Они могут продолжать создавать с помощью эталонных сборок и средств, установленных с помощью пакета VS SDK.
