---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 52d01cfc3ae6a453330c2dda5da137f449ff5cbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
Восстанавливает параметры по умолчанию [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и автоматически запускает интегрированную среду разработки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. При необходимости выполняет сброс параметров в соответствии с указанным файлом VSSETTINGS.  
  
 Параметры по умолчанию определяются по профилю, который был выбран при первом запуске [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Аргументы  
 `SettingsFile`  
 Полный путь и имя VSSETTINGS-файла, применяемого к [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  
  
 Чтобы восстановить профиль "Общие параметры разработки", используйте `General`.  
  
## <a name="remarks"></a>Примечания  
 Если файл `SettingsFile` не указан, при следующем запуске [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] вам будет предложено выбрать коллекцию параметров по умолчанию.  
  
## <a name="example"></a>Пример  
 Следующая команда применяет параметры, сохраненные в файле `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>См. также  
 [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)