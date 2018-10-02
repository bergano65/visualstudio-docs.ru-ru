---
title: 'Ошибка: SQL может&#39;t обнаружить компонент SSDEBUGPS | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1782412ded2c4edff0da29b13160107664170d20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571108"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Ошибка: SQL может&#39;t обнаружить компонент SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ошибка: SQL можно&#39;t найти компонент SSDEBUGPS](https://docs.microsoft.com/visualstudio/debugger/error-sql-can-t-find-ssdebugps).  
  
Файл SSDEBUGPS.dll — компонент узла отладки SQL Server.  
  
 Эта ошибка возникает при попытке запустить отладку и указывает, что указанный файл не удается обнаружить на компьютере [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. Существуют две возможные причины этого: установка удаленной отладки не выполнялась или по каким-либо иным причинам файл был удален.  
  
 Существует два способа, чтобы устранить эту ошибку: повторное выполнение установки удаленной отладки и копирование файла на [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] машины.  
  
 Повторное выполнение установки удаленной отладки, следуйте инструкциям в [удаленной отладки](../debugger/remote-debugging.md).  
  
 Если есть возможность найти копию ssdebugps.dll, можно скопировать его на [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] машины. Этот файл должен быть в каталоге \Program Files\ Common Files\Microsoft Shared\SQL Debugging. Может оказаться на другом [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] компьютере или на компьютере, который имеет [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] установлен.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Копирование файла SSDEBUGPS.dll на компьютер SQL Server 2005  
  
1.  Скопируйте файл в каталог с тем же именем и путем на [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] машины.  
  
2.  Зарегистрировать его, открыв **командной**и выполнив следующую команду:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```



