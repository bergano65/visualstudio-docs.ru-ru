---
title: "Окна инструментов в реестре | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 12
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: dc99605a367bb3584f9766b50aa2a4ff382656c4
ms.lasthandoff: 02/22/2017

---
# <a name="tool-windows-in-the-registry"></a>Окна инструментов в реестре
Пакеты VSPackage, которые предоставляют средства windows, необходимо зарегистрировать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] как средство поставщиков окна. Окна инструментов, созданные с помощью шаблона пакета Visual Studio для этого по умолчанию. Средство окна поставщики имеют разделы реестра системы, указать видимость атрибуты, такие как размер окна по умолчанию средство и расположение, GUID, которая предоставляет панель инструментов окна и стиля закрепления окна.  
  
 Во время разработки поставщиков управляемых инструментов окна зарегистрировать средство windows, добавление атрибутов в исходном коде и затем запустив программу RegPkg.exe на результирующую сборку. Дополнительные сведения см. в разделе [регистрация окно инструментов](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Регистрация поставщиков неуправляемые средство окна  
 Неуправляемые средство поставщиков окна, необходимо зарегистрировать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в разделе ToolWindows в системный реестр. В следующем фрагменте файла .reg показано, как окно динамическое средство может быть зарегистрировано.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 В разделе первого в приведенном выше примере номер версии — это версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], например 7.1 или 8.0 подраздел {f0e1e9a1-9860-484d-ad5d-367d79aabf55} является GUID на панели инструментов окна (DynamicWindowPane) и значение по умолчанию {01069cdd-95ce-4620-ac21-ddff6c57f012} является GUID VSPackage, предоставляя окно инструментов. Объяснение Float и DontForceCreate подразделов в разделе [конфигурации отображения окна средства](../extensibility/tool-window-display-configuration.md).  
  
 Второй необязательный ключ ToolWindows\Visibility, указывает идентификаторы GUID команды, требующие окно средства будут сделаны видимыми. В этом случае существует команды не указан. Дополнительные сведения см. в разделе [конфигурации отображения окна средства](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Основные сведения о пакетах VSPackage](../misc/vspackage-essentials.md)
