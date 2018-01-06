---
title: "Определение требований к системе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: "50"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dc16c51b72ced37072c4ddf6d47bf347cf57c0f8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="detecting-system-requirements"></a>Определение требований к системе
Пакет VSPackage не может работать, если не установлена среда Visual Studio. При использовании установщика Windows для управления установкой VSPackage можно настроить установщик для обнаружения установки Visual Studio. Можно также настроить его для поиска системы для требований других, например, определенной версии Windows или определенный объем оперативной памяти.  
  
## <a name="detecting-visual-studio-editions"></a>Обнаружение выпуски Visual Studio  
 Чтобы определить, установлен ли выпуск Visual Studio, проверьте значение раздела реестра установки (REG_DWORD) 1 в соответствующей папке, перечисленные в следующей таблице. Обратите внимание, что иерархия выпуски Visual Studio:  
  
1.  Предприятие  
  
2.  Professional  
  
3.  Сообщество  
  
 При установке «выше» выпуск добавляются разделы реестра для этого выпуска, также как и для «ниже» выпуски. То есть если установлен выпуск Enterprise edition, ключ установки равен 1 для предприятия, а также в выпусках Professional и Community. Поэтому необходимо проверять только выпуск «высокий», необходимые.  
  
> [!NOTE]
>  32-разрядные ключи в 64-разрядной версии редактора реестра, указанных в списке HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. Ключи Visual Studio находятся в HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Продукт|Ключ|  
|-------------|---------|  
|Visual Studio Enterprise|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (интегрированной и изолированные)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Обнаружение при запуске Visual Studio  
 VSPackage не зарегистрирован должным образом, если при установке VSPackage работает Visual Studio. Программа установки должна обнаружить, когда выполняется Visual Studio и отклонять для установки программы. Установщик Windows не позволяет использовать записи таблицы для включения такого обнаружения. Вместо этого необходимо создать пользовательское действие, следующим образом: используйте `EnumProcesses` функции обнаружения процесса devenv.exe и либо задайте для свойства установщика, используемого в условии запуска или условно отображать диалоговое окно, позволяющее пользователю закрыть Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)