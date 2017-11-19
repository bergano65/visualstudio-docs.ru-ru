---
title: "Как: миграция расширяемость проектов Visual Studio 2015 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 016e609acb7ad837580b4cabb6055169ac7357c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Как: миграция расширяемость проектов Visual Studio 2015
Вот как можно обновить расширения.  
  
> [!IMPORTANT]
>  Если планируется поддерживать версии решения расширения для более ранней версии Visual Studio, не забудьте создать копию перед обновлением. Часто бывает трудно вернуться в предыдущее состояние обновленной версии.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Чтобы обновить решение расширяемости  
  
1.  С помощью копии, необходимо обновить, откройте его в новой версии. Пользователю будет рекомендовано обновления операция необратима.  
  
2.  После завершения обновления, измените путь внешней программы до новой версии программы devenv.exe. Щелкните правой кнопкой мыши узел проекта в **обозревателе решений**, затем выберите **свойства**. В **отладки** , найдите текстовое поле с **запуск внешней программы** и измените путь к devenv.exe в Visual Studio 2015 путь, который должен выглядеть примерно следующим образом:  
  
     **14.0\Common7\IDE\devenv.exe %ProgramFiles%\Microsoft visual Studio**  
  
3.  Добавьте ссылку на Microsoft.VisualStudio.Shell.14.0.dll. (Щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите **добавьте / Reference**. Выберите **расширения** вкладку, а затем установите флажок **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Постройте решение. Для развертывания файлов сборки:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< создать имя\>\\< имя проекта\>\\< версия проекта\> \\** .  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Для обновления проекта расширяемости NuGet VS SDK ссылок на сборки  
  
1.  Определите VS SDK ссылочные сборки, необходимые для проекта.  В **обозревателе решений**, разверните узел проекта **ссылки** узел и просмотрите список ссылок проекта.  Ссылки на сборки VS SDK будет иметь префикс **Microsoft.VisualStudio** в имени (например: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Удалить ссылочные сборки VS SDK из проекта, выберите их, щелкните правой кнопкой мыши и **удалить**.  
  
3.  Добавьте NuGet версии ссылочных сборок VS SDK.  Оставаясь в **ссылки обозревателя решений** открытым узлом **управление пакетами NuGet...**  диалогового окна.  Если вы хотите узнать больше об этом диалоговом окне, см. раздел [пользовательского интерфейса диспетчера пакетов](http://docs.microsoft.com/NuGet/Tools/Package-Manager-UI). Ссылочные сборки VS SDK публикуются на [nuget.org](http://www.nuget.org) по [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  С помощью **nuget.org** как вашей **источник пакета**, поиск по имени пакета NuGet, удовлетворяющее необходимая ссылка сборки (например: Microsoft.VisualStudio.Shell.14.0) и установите его в вашей проект.  NuGet может добавить несколько ссылочных сборок для удовлетворения зависимостей исходную сборку.  
  
     При желании можно добавить все ссылочные сборки VS SDK за один раз, установка пакета SDK для VS [Meta пакета](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Вы также можете переключить с помощью NuGet версии средств сборки пакета SDK для VS. Этот пакет NuGet является [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) и один раз добавляется проект необходимо добавить необходимые средства и файлы для позволяют создавать расширения проекта на компьютере без установленный пакет SDK для VS.  
  
> [!NOTE]
>  Это не требуется обновить существующие проекты расширения среды для использования NuGet ссылочные сборки и средства.  Они смогут продолжить для построения с помощью ссылочных сборок и средств, устанавливаемых с VS SDK.