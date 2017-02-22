---
title: "Регистрация обработчиков команд сборки взаимодействия | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "сборки взаимодействия, обработчики команд"
  - "Обработка с использованием сборок взаимодействия, регистрация команд"
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Регистрация обработчиков команд сборки взаимодействия
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Необходимо зарегистрировать VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] таким образом, интегрированную среду разработки \(IDE\) правильно направляет его команды.  
  
 Можно обновить реестр, изменив вручную или с помощью файла регистрации \(RGS\-\). Для получения дополнительной информации см. [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
 Управляемые пакета Framework \(MPF\) предоставляет следующие функциональные возможности через <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> класса.  
  
 [Command Table Format Reference](http://msdn.microsoft.com/ru-ru/09e9c6ef-9863-48de-9483-d45b7b7c798f) ресурсы находятся в неуправляемых библиотек спутниковой связи DLL пользовательского интерфейса.  
  
## Регистрация обработчика команды VSPackage  
 VSPackage, выступающий в качестве обработчика для пользовательского интерфейса \(UI\) — на основе команды требуется запись реестра с именем VSPackage `GUID`. Этот параметр реестра указывает расположение файла ресурсов VSPackage пользовательского интерфейса и ресурсов меню в файле. Запись реестра, сам находится в разделе HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\*\< версия \>*\\Menus, где *\< версия \>* версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], например 9.0.  
  
> [!NOTE]
>  Путь к корневому каталогу HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< версия \>* может быть переопределен с альтернативной корневых при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] инициализируется оболочки. Дополнительные сведения о корневой путь в разделе [Установка пакетов VSPackages с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### Запись реестра CTMENU ресурсов  
 Структура записи реестра выглядит так:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\ Menus\ <GUID> = <Resource Information>  
```  
  
 \<*GUID*\> является `GUID` из VSPackage в форме {XXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXX}.  
  
 *\< сведения о ресурсе \>* состоит из трех элементов, разделенных запятыми. Эти элементы расположены в порядке:  
  
 \<*Путь к DLL ресурсов*\>, \<*идентификатор ресурса меню*\>, \<*версии меню*\>  
  
 В следующей таблице описаны поля \<*сведения о ресурсах*\>.  
  
|Элемент|Описание|  
|-------------|--------------|  
|\<*Путь к DLL ресурсов*\>|Это полный путь к ресурсу библиотеки DLL, содержащей ресурс меню или указан, означающее, что VSPackage ресурс библиотеки DLL для использования \(как указано в подразделе пакеты, где зарегистрирован VSPackage, сам\).<br /><br /> Обычно это поле оставить пустым.|  
|\<*Идентификатор ресурса меню*\>|Это идентификатор ресурса `CTMENU` ресурс, который содержит все элементы пользовательского интерфейса для VSPackage при компиляции из [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) файла.|  
|\<*Версии меню*\>|Это число, используемое в качестве версии для `CTMENU` ресурсов.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Это значение используется для определения, если нужно произвести повторное слияние содержимого `CTMENU` ресурсов с помощью своего кэша всех `CTMENU` ресурсов. Произвести повторное слияние запускается с помощью команды devenv установки.<br /><br /> Это значение следует изначально задано значение 1 и увеличивается на единицу после каждого изменения в `CTMENU` ресурсов и до произвести повторное слияние.|  
  
### Пример  
 Вот пример несколько записей ресурсов:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\ Menus\ {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10 {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды и меню, использования сборок взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)