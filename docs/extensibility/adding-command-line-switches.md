---
title: "Добавление параметров командной строки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d686e7b68e790c419679bf495bf08ad4cd4807e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="adding-command-line-switches"></a>Добавление параметров командной строки
Можно добавить параметры командной строки, применимые к файлу пакета VSPackage, при выполнении devenv.exe. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> для объявления имени параметра и его свойств. В этом примере для подкласс пакет VSPackage с именем добавляется параметр MySwitch **AddCommandSwitchPackage** без аргументов и с VSPackage, загружаются автоматически.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 В следующей таблице показаны именованные параметры  
  
 Аргументы  
 Число аргументов для коммутатора. Может быть «*», или список аргументов.  
  
 DemandLoad  
 Пакет VSPackage загружаются автоматически, если он равен 1, в противном случае значение равно 0.  
  
 HelpString  
 Строка или ресурс идентификатор справки строки для отображения с **devenv /?**.  
  
 name  
 Переключатель.  
  
 PackageGuid  
 Идентификатор GUID пакета.  
  
 Первое значение аргументы обычно 0 или 1. Специальное значение "*" можно указать, что весь остаток командной строке аргумент. Это может быть полезна для отладки сценариев, где пользователь должен попасть в командной строке отладчика.  
  
 Значение DemandLoad `true` (1) или `false` (0) указывает, что VSPackage должны загружаться автоматически.  
  
 HelpString значение — это идентификатор ресурса строки, который отображается в devenv /? Отображение справки. Это значение должно быть в форме «#nnn» где nnn является целым числом. Строковое значение в файле ресурсов должен оканчиваться на символ новой строки.  
  
 Значение Name — имя коммутатора.  
  
 Значение PackageGuid — идентификатор GUID пакета, который реализует этот переключатель. Интегрированная среда разработки использует этот идентификатор GUID для поиска VSPackage в реестре, к которому применяется параметр командной строки.  
  
## <a name="retrieving-command-line-switches"></a>Получение параметров командной строки  
 При загрузке пакета параметров командной строки можно получить, выполнив следующие действия.  
  
1.  В пакете VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализацию, вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> для получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> интерфейса.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> для получения параметров командной строки, введенные пользователем.  
  
 Ниже показано, как узнать ли параметр командной строки MySwitch было введено пользователем:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Для проверки параметров командной строки каждый раз, когда загружается пакет вашей обязанностью является.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Параметры командной строки для команды Devenv](../ide/reference/devenv-command-line-switches.md)   
 [Программа CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [. Файлах pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)