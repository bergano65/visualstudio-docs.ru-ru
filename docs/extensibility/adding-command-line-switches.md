---
title: "Добавление параметров командной строки | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "параметры командной строки, добавление"
  - "параметры командной строки, извлечение"
  - "Метод IVsAppCommandLine::GetOption"
  - "параметры командной строки"
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Добавление параметров командной строки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно добавить параметры командной строки, которые применяются к VSPackage при выполнении devenv.exe. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> для объявления имени параметра и его свойств. В этом примере добавляется параметр MySwitch для подкласса VSPackage с именем **AddCommandSwitchPackage** без аргументов и с автоматической загрузки VSPackage.  
  
```c#  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 В следующей таблице показаны именованные параметры  
  
 Аргументы  
 Число аргументов для коммутатора. Может быть «\*», или список аргументов.  
  
 DemandLoad  
 Автоматически Загрузите VSPackage, если он равен 1, в противном случае — значение 0.  
  
 HelpString  
 Строка или ресурс идентификатор справки строки для отображения с **devenv \/?**.  
  
 Имя  
 Ключ.  
  
 PackageGuid  
 Идентификатор GUID пакета.  
  
 Значение первого аргумента обычно 0 или 1. Специальное значение "\*" может использоваться для указания аргументом является весь остаток командной строки. Это может быть полезно для отладки сценариев, где пользователь должен пройти в командной строке отладчика.  
  
 Значение DemandLoad `true` \(1\) или `false` \(0\) указывает, что VSPackage должны загружаться автоматически.  
  
 HelpString значение — это идентификатор ресурса строки, которая отображается в devenv \/? Отображение справки. Это значение должно быть в форме «\#nnn» где nnn — целое число. Строковое значение в файле ресурсов должен заканчиваться символ новой строки.  
  
 Значение Name — имя коммутатора.  
  
 Значение параметра PackageGuid — идентификатор GUID пакета, который реализует этот ключ. Интегрированная среда разработки использует этот идентификатор GUID для поиска VSPackage в реестре, к которому применяется параметр командной строки.  
  
## Получение параметров командной строки  
 При загрузке пакета параметры командной строки можно получить, выполнив следующие действия.  
  
1.  В вашей VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализацию, вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> для получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> интерфейса.  
  
2.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> для получения параметров командной строки, введенные пользователем.  
  
 Ниже показано, как узнать ли параметр командной строки MySwitch было введено пользователем:  
  
```c#  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine)); int isPresent = 0; string optionValue = ""; cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Это ответственность для проверки параметров командной строки каждого время загрузки пакета.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Параметры командной строки для команды Devenv](../ide/reference/devenv-command-line-switches.md)   
 [Служебная программа CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [. Файлы pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)