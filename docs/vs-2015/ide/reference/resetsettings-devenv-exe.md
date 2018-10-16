---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 276205ae2aab3c38ceb3d4f1419e0bac13ae626c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273498"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Восстанавливает параметры по умолчанию [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и автоматически запускает интегрированную среду разработки [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. При необходимости выполняет сброс параметров в соответствии с указанным файлом VSSETTINGS.  
  
 Параметры по умолчанию определяются по профилю, который был выбран при первом запуске [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Аргументы  
 `SettingsFile`  
 Полный путь и имя VSSETTINGS-файла, применяемого к [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]  
  
 Чтобы восстановить профиль "Общие параметры разработки", используйте `General`.  
  
## <a name="remarks"></a>Примечания  
 Если файл `SettingsFile` не указан, при следующем запуске [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] вам будет предложено выбрать коллекцию параметров по умолчанию.  
  
## <a name="example"></a>Пример  
 Следующая команда применяет параметры, сохраненные в файле `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)



