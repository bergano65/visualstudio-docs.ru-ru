---
title: Окна инструментов в реестре | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 234a3f50865e77f2c6b5a4057e6766b26d7ff521
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="tool-windows-in-the-registry"></a>Окна инструментов в реестре
Необходимо зарегистрировать пакетов VSPackage, предоставляющих окна инструментов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] как средство поставщиков окна. Окна инструментов, созданные с помощью шаблона пакета Visual Studio для этого по умолчанию. Поставщиков окна инструментов, используют разделы реестра системы, определяющие видимость атрибутов, таких как размер окна по умолчанию средство и расположение, GUID, выполняющий область окна инструментов и стиль закрепления окна.  
  
 Во время разработки поставщики управляемых инструментов окна зарегистрировать окна инструментов путем добавления атрибутов к исходному коду, а затем запустить служебную программу RegPkg.exe в результирующей сборке. Дополнительные сведения см. в разделе [регистрации окно инструментов](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Регистрация поставщиков окна неуправляемые средства  
 Неуправляемые средство поставщиков окна, необходимо зарегистрировать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в разделе ToolWindows в системный реестр. Следующие фрагменте REG-файла показано, как может быть зарегистрировано в окно инструментов динамического:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 В первый ключ, в приведенном выше примере, номер версии — версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], такие как 7.1 или 8.0, подраздел {f0e1e9a1-9860-484d-ad5d-367d79aabf55} — это GUID панели окна инструментов (DynamicWindowPane), а также {значение по умолчанию 01069cdd-95ce-4620-ac21-ddff6c57f012} является GUID пакета VSPackage, предоставляя окно инструментов. Объяснение Float и DontForceCreate подразделы в разделе [конфигурации отображения окна средства](../extensibility/tool-window-display-configuration.md).  
  
 Второй необязательный ключ ToolWindows\Visibility, указывает идентификаторы GUID команд, требующих окна инструментов, чтобы сделать видимым. В этом случае существует команды не указан. Дополнительные сведения см. в разделе [конфигурации отображения окна средства](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)