---
title: "Ошибка:, SQL может &#39; удается найти компонент SSDEBUGPS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43a437cfc4be1c9168b16e4b9d1a46e2eadcb2e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Ошибка:, SQL может &#39; удается найти компонент SSDEBUGPS
Файл SSDEBUGPS.dll — компонент узла отладки SQL Server.  
  
 Эта ошибка возникает при попытке запустить отладку и указывает, что указанный файл не удается обнаружить на компьютере [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Существуют две возможные причины этого: установка удаленной отладки не выполнялась или по каким-либо иным причинам файл был удален.  
  
 Существует два способа, чтобы устранить эту ошибку: повторное выполнение установки удаленной отладки и копирование файла на [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] машины.  
  
 Повторное выполнение установки удаленной отладки, следуйте инструкциям в [удаленной отладки](../debugger/remote-debugging.md).  
  
 Если есть возможность найти копию ssdebugps.dll, можно скопировать его на [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] машины. Этот файл должен быть в каталоге \Program Files\ Common Files\Microsoft Shared\SQL Debugging. Может оказаться на другом [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] компьютере, или на компьютере, где [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] установлен.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Копирование файла SSDEBUGPS.dll на компьютер SQL Server 2005  
  
1.  Скопируйте файл в каталог с тем же именем и путем на [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] машины.  
  
2.  Зарегистрируйте его, открыв **командной строки**и выполнив следующую команду:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```