---
title: Регистрация обработчиков команд сборки взаимодействия | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a4b2c0d40029cbc84d64a4ffe5ee50c59c893b95
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131914"
---
# <a name="registering-interop-assembly-command-handlers"></a>Регистрация обработчиков команд сборки взаимодействия
Необходимо зарегистрировать VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , чтобы интегрированной среды разработки (IDE) правильно перенаправляет его команды.  
  
 Можно обновить реестр, путем редактирования вручную или с помощью файла регистратора (RGS-). Дополнительные сведения см. в разделе [Создание скриптов регистратора](/cpp/atl/creating-registrar-scripts).  
  
 Managed Package Framework (MPF) предоставляет следующие функциональные возможности через <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> класса.  
  
 [Команда ссылка на формат таблицы](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f) ресурсы находятся в неуправляемых библиотек спутниковой связи DLL пользовательского интерфейса.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Команда регистрации обработчика пакета VSPackage  
 Пакет VSPackage, выступающего в качестве обработчика для пользовательского интерфейса (UI) — на основе команды требуется запись реестра с именем VSPackage `GUID`. Эта запись реестра указывает расположение файла ресурсов пользовательского интерфейса в пакете VSPackage и ресурс меню в этом файле. Параметр реестра сам находится в папке HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<версии >* \Menus, где  *\<версии >* версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], например 9.0.  
  
> [!NOTE]
>  Путь к корневому каталогу HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<версии >* может быть переопределен с альтернативной корневой при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] инициализируется оболочки. Дополнительные сведения о корневой путь в разделе [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>Запись реестра CTMENU ресурсов  
 Структура записи реестра выглядит так:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*Идентификатор GUID*> является `GUID` пакета VSPackage в форме {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Сведения о ресурсах >* состоит из трех элементов, разделенных запятыми. Эти элементы располагаются в порядке:  
  
 \<*Путь к DLL-Библиотека ресурсов*>, \< *идентификатор ресурса меню*>, \< *версии меню*>  
  
 В следующей таблице описаны поля \< *сведения о ресурсах*>.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|\<*Путь к DLL-Библиотека ресурсов*>|Это полный путь к DLL, содержащую ресурс меню ресурса или указан, указание того, что в пакете VSPackage ресурсов DLL для использования (как указано в подразделе пакеты, где зарегистрирован сам пакет VSPackage).<br /><br /> Обычно это поле оставить пустым.|  
|\<*Идентификатор ресурса меню*>|Это идентификатор ресурса `CTMENU` ресурс, который содержит все элементы пользовательского интерфейса для VSPackage как откомпилирован из [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) файла.|  
|\<*Версия меню*>|Это число, используемое в качестве версии для `CTMENU` ресурсов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Это значение используется для определения того, ему следует произвести повторное слияние содержимого `CTMENU` ресурсов с использованием своего кэша всех `CTMENU` ресурсов. Произвести повторное слияние инициируется, выполнив команду setup devenv.<br /><br /> Это значение следует изначально задано значение 1 и увеличивается на единицу после каждого изменения в `CTMENU` ресурсов и перед инициализацией произвести повторное слияние.|  
  
### <a name="example"></a>Пример  
 Ниже приведен пример несколько записей ресурсов:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды и меню, которые используют сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)