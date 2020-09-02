---
title: Окна инструментов в реестре | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186388"
---
# <a name="tool-windows-in-the-registry"></a>Окно инструментов в реестре
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакеты VSPackage, предоставляющие окна инструментов, должны регистрироваться в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] качестве поставщиков окон инструментов. Окна инструментов, созданные с помощью шаблона пакета Visual Studio, по умолчанию выполняют эту задачу. Поставщики окон инструментов имеют разделы системного реестра, которые задают атрибуты видимости, такие как размер окна инструментов по умолчанию и расположение, идентификатор GUID окна, служащего областью окна инструментов, и закрепление стиля.  
  
 Во время разработки управляемые поставщики окон инструментов регистрируют окна инструментов, добавляя атрибуты в исходный код, а затем запуская служебную программу RegPkg.exe в полученной сборке. Дополнительные сведения см. [в разделе Регистрация окна инструментов](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Регистрация неуправляемых поставщиков окон инструментов  
 Поставщики окон неуправляемых средств должны быть зарегистрированы [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] в разделе тулвиндовс системного реестра. В следующем фрагменте REG-файла показано, как можно зарегистрировать Динамическое окно инструментов:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 В первом ключе в приведенном выше примере номер версии — это версия [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , например 7,1 или 8,0, подраздел {f0e1e9a1-9860-484d-ad5d-367d79aabf55} — это идентификатор GUID панели окна инструментов (динамиквиндовпане), а значение по умолчанию {01069cdd-95ce-4620-ac21-ddff6c57f012} — это идентификатор GUID пакета VSPackage, предоставляющего окно инструментов. Описание подразделов float и Донтфорцекреате см. в разделе [Настройка экрана окна инструментов](../extensibility/tool-window-display-configuration.md).  
  
 Второй необязательный ключ, Тулвиндовс\висибилити, указывает идентификаторы GUID команд, для которых необходимо, чтобы окно инструментов было сделано видимым. В этом случае команды не указаны. Дополнительные сведения см. в разделе [Настройка экрана окна инструментов](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о пакетах VSPackage](../misc/vspackage-essentials.md)
