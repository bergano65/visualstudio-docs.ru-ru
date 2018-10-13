---
title: Перечислители | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4dcc660ba5aacf1b8014e7c4ca15443f2fdf881b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258509"
---
# <a name="enumerators"></a>Перечислители
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе перечислены типы данных перечислителя в API подключаемого модуля управления источник, подключаемый модуль системы управления версиями необходимо знать.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Код команды](../extensibility/command-code-enumerator.md)  
 Перечисляет параметры для [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [SccPopulateList](../extensibility/sccpopulatelist-function.md) функции.  
  
 [Сообщение](../extensibility/message-enumerator.md)  
 Перечисляет флаги, используемые для печати обратного вызова, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)  
 Содержит именованные константы, определяющие состояние файла в системе управления версиями.  
  
 [Код состояния каталога](../extensibility/directory-status-code-enumerator.md)  
 Содержит именованные константы, определяющие состояние каталога в системе управления версиями.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Определяет пакет SDK подключаемого модуля управления источника и описывает включаемые ресурсы.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Запрашивает у пользователя Дополнительные параметры для данной команды.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Проверяет список файлов для их текущее состояние. Кроме того, использует `pfnPopulate` функция уведомляет вызывающего объекта, если файл не соответствует критериям для `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Описывает функцию обратного вызова, используемый [SccOpenProject](../extensibility/sccopenproject-function.md) для отображения сообщений из системы управления версиями, подключаемый модуль через среду IDE.  
  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)  
 Предоставляет полный список всех элементов в API подключаемых модулей управления источника.

