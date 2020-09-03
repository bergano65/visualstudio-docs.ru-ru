---
title: 'Ошибка: SQL не удается обнаружить компонент SSDEBUGPS | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25462a99bd3e773f03af3918a9e25d11ed006c1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185208"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Ошибка: SQL не удается обнаружить компонент SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Файл SSDEBUGPS.dll — компонент узла отладки SQL Server.  
  
 Эта ошибка возникает при попытке запустить отладку и указывает, что указанный файл не удается обнаружить на компьютере [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. Существуют две возможные причины этого: установка удаленной отладки не выполнялась или по каким-либо иным причинам файл был удален.  
  
 Существуют два способа разрешить эту проблему: повторное выполнение установки удаленной отладки и копирование файла на компьютер [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)].  
  
 Чтобы выполнить повторный запуск установки удаленной отладки, следуйте инструкциям в статье [Удаленная отладка](../debugger/remote-debugging.md).  
  
 Если есть возможность найти копию файла ssdebugps.dll, можно скопировать этот файл на компьютер [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. Этот файл должен быть в каталоге \Program Files\ Common Files\Microsoft Shared\SQL Debugging. Он может находиться на другом [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] компьютере или на компьютере, на котором [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] установлен.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Копирование файла SSDEBUGPS.dll на компьютер SQL Server 2005  
  
1. Скопируйте файл в каталог с тем же именем и путем на компьютер [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)].  
  
2. Зарегистрируйте этот файл, запустив **Командную строку** и выполнив следующую команду:  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```
