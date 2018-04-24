---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22dd925755e996a927664e0a9a5846fc10247882
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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