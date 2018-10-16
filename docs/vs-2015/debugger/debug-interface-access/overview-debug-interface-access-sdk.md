---
title: Обзор (доступа к интерфейсу отладки пакета SDK) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 741e4ee8e7b05db9d8b63b296569e268d7144dc7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193613"
---
# <a name="overview-debug-interface-access-sdk"></a>Общие сведения (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Используйте пакет SDK для доступа к данным отладки Microsoft. Пакет SDK для доступа к интерфейсу отладки предоставляет COM набор API, который избавляет от необходимости изменять код каждый раз, когда Майкрософт изменяет формат отладочной информации. Пакет SDK для доступа к интерфейсу отладки также позволяет считывать из набор select отладочной информации в PDB-файл и .dbg файлы, созданные на предыдущих версиях [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 5.0 и более поздних версиях.  
  
 Каждый интерфейс в пакете SDK для доступа к интерфейсу отладки представляет объект COM, за исключением там, где указано обратное. Дополнительные интерфейсы и тем самым дополнительные объекты, созданные с помощью явных запросов, такие как [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) или [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), а не путем вызова `QueryInterface` на существующие указатели интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)



