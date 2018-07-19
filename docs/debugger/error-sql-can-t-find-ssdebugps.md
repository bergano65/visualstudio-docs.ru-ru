---
title: 'Ошибка: SQL может&#39;t обнаружить компонент SSDEBUGPS | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1498a287bdb474751dfaa5b4b23c30bc302544e7
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058260"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Ошибка: SQL может&#39;t обнаружить компонент SSDEBUGPS

Файл SSDEBUGPS.dll — компонент узла отладки SQL Server.

Эта ошибка возникает при попытке запустить отладку и указывает, что указанный файл не удается обнаружить на компьютере [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Существуют две возможные причины этого: установка удаленной отладки не выполнялась или по каким-либо иным причинам файл был удален.

Существует два способа, чтобы устранить эту ошибку: повторное выполнение установки удаленной отладки и копирование файла на [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] машины.

Повторное выполнение установки удаленной отладки, следуйте инструкциям в [удаленной отладки](../debugger/remote-debugging.md).

Если есть возможность найти копию ssdebugps.dll, можно скопировать его на [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] машины. Этот файл должен быть в каталоге \Program Files\ Common Files\Microsoft Shared\SQL Debugging. Может оказаться на другом [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] компьютере или на компьютере с Visual Studio 2005 и.

Копирование файла SSDEBUGPS.dll на компьютер с SQL Server 2005:

1. Скопируйте файл в каталог с тем же именем и путем на [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] машины.

2. Зарегистрировать его, открыв **командной**и выполнив следующую команду:

    ```cmd
    regsrv32 ssdebugps.dll
    ```
