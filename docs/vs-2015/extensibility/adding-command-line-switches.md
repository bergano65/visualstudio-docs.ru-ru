---
title: Добавление параметров командной строки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991336"
---
# <a name="adding-command-line-switches"></a>Добавление параметров командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете добавить параметры командной строки, которые применяются к VSPackage при выполнении devenv.exe. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> для объявления имени параметра и его свойств. В этом примере добавляется параметр MySwitch для подкласса VSPackage с именем **AddCommandSwitchPackage** без аргументов и с пакетом VSPackage, загружаются автоматически.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 В следующей таблице показаны именованные параметры  
  
 Аргументы  
 Число аргументов для параметра. Может быть «*», или список аргументов.  
  
 DemandLoad  
 Загрузите пакет VSPackage автоматически, если задано значение 1, в противном случае — значение 0.  
  
 HelpString  
 Строка или ресурс идентификатор справки строки для отображения с **devenv /?**.  
  
 name  
 Переключатель.  
  
 PackageGuid  
 Идентификатор GUID пакета.  
  
 Первое значение аргументов обычно 0 или 1. Специальное значение "*" может использоваться для указания, что весь остаток командной строки — это аргумент. Это может быть полезно для отладки сценариев, где пользователь должен пройти в командной строке отладчика.  
  
 Имеет значение DemandLoad `true` (1) или `false` (0) указывает, что VSPackage должны загружаться автоматически.  
  
 HelpString значение — идентификатор ресурса строки в devenv /? Отображение справки. Это значение должно быть в форме «#nnn» где nnn — целое число. Строковое значение в файле ресурсов должна завершиться в символ новой строки.  
  
 Значение имени является имя коммутатора.  
  
 Значение PackageGuid – идентификатор GUID пакета, который реализует этот переключатель. Интегрированная среда разработки использует этот идентификатор GUID для поиска VSPackage в реестре, к которому применяется параметр командной строки.  
  
## <a name="retrieving-command-line-switches"></a>Получение параметров командной строки  
 Когда загружается пакет, параметры командной строки можно получить, выполнив следующие действия.  
  
1. В ваш VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации, вызов `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> для получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> интерфейс.  
  
2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> для получения параметров командной строки, введенные пользователем.  
  
   Приведенный ниже показано, как узнать ли параметра командной строки MySwitch введенный пользователем:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Отвечает на наличие параметров командной строки каждый раз, когда загружается пакет.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Параметры командной строки для команды Devenv](../ide/reference/devenv-command-line-switches.md)   
 [Служебная программа CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [Файлы .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
