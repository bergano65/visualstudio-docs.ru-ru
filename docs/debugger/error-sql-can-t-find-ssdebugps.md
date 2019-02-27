---
title: 'Ошибка: SQL может&#39;t обнаружить компонент SSDEBUGPS | Документация Майкрософт'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 854105ea5d94f6d3b09ce73a23ec45ccab9e797c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694170"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Ошибка: SQL может&#39;t обнаружить компонент SSDEBUGPS

Файл SSDEBUGPS.dll — компонент узла отладки SQL Server.

Эта ошибка возникает при попытке запустить отладку и указывает, что указанный файл не удается обнаружить на компьютере [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Существуют две возможные причины этого: установка удаленной отладки не выполнялась или по каким-либо иным причинам файл был удален.

Существуют два способа разрешить эту проблему: повторное выполнение установки удаленной отладки и копирование файла на компьютер [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

Повторное выполнение установки удаленной отладки, следуйте инструкциям в [удаленной отладки](../debugger/remote-debugging.md).

Если есть возможность найти копию файла ssdebugps.dll, можно скопировать этот файл на компьютер [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Этот файл должен быть в каталоге \Program Files\ Common Files\Microsoft Shared\SQL Debugging. Может оказаться на другом [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] компьютере или на компьютере с Visual Studio 2005 и.

Копирование файла SSDEBUGPS.dll на компьютер SQL Server 2005:

1. Скопируйте файл в каталог с тем же именем и путем на компьютер [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

2. Зарегистрируйте этот файл, запустив **Командную строку** и выполнив следующую команду:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
