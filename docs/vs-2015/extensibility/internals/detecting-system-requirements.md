---
title: Определение требований к системе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 467554b8e50878bcdf1029e4792bbf168a09fa11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842493"
---
# <a name="detecting-system-requirements"></a>Определение требований к системе
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакет VSPackage не может работать, если не установлена Visual Studio. При использовании установщик Windows Майкрософт для управления установкой пакета VSPackage можно настроить установщик, чтобы определить, установлена ли Visual Studio. Кроме того, его можно настроить для проверки системы на наличие других требований, например конкретной версии Windows или определенного объема ОЗУ.  
  
## <a name="detecting-visual-studio-editions"></a>Обнаружение выпусков Visual Studio  
 Чтобы определить, установлен ли выпуск Visual Studio, убедитесь, что значение раздела реестра Install — (REG_DWORD) 1 в соответствующей папке, как указано в следующей таблице. Обратите внимание, что существует иерархия выпусков Visual Studio:  
  
1. Enterprise  
  
2. Professional  
  
3. Сообщество  
  
   При установке выпуска "более поздней версии" добавляются разделы реестра для этого выпуска, а также для "нижних" выпусков. То есть если установлен выпуск Enterprise Edition, то для ключа установки устанавливается значение 1 для Enterprise, а также для выпусков Professional и Community. Поэтому необходимо проверить только наличие необходимого выпуска.  
  
> [!NOTE]
> В 64-разрядной версии редактора реестра 32-разрядные ключи отображаются в разделе HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node \\ . Ключи Visual Studio находятся в разделе HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing \\ .  
  
|Продукт|Ключ|  
|-------------|---------|  
|Visual Studio Enterprise|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Оболочка Visual Studio 2015 (интегрированная и изолированная)|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Определение времени выполнения Visual Studio  
 Невозможно правильно зарегистрировать VSPackage, если Visual Studio работает при установке VSPackage. Установщик должен определить, когда работает Visual Studio, а затем отказаться от установки программы. Установщик Windows не позволяет использовать записи таблицы для включения такого обнаружения. Вместо этого необходимо создать пользовательское действие следующим образом: использовать `EnumProcesses` функцию для обнаружения devenv.exe процесса, а затем либо задать свойство установщика, которое используется в условии запуска, либо условно отобразить диалоговое окно, предлагающее пользователю закрыть Visual Studio.  
  
## <a name="see-also"></a>См. также:  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
