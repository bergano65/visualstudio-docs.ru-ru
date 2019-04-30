---
title: Удаление сведений системы управления версиями из. Proj и. SLN-файлов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4caa3d9edd7cba768f6338ad7aecf168041a1130
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859175"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Удаление сведений системы управления версиями из файлов PROJ и SLN
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В версии 1.2 API подключаемых модулей управления источника SCC хранится в MSSCCPRJ. Файл SCC. Преимущество MSSCCPRJ. Файл SCC —, которое SCC сведения не исходные - контролируется, как в файлов proj и SLN.  
  
## <a name="version-12-changes"></a>Изменения в версии 1.2  
 В исходный элемент управления подключаемые модули, основанные на API подключаемых модулей управления исходной версии 1.1 сведения о системе управления версиями, хранится в проекта (.proj) и файлов решения (SLN). AuxPath указывается расположение базы данных сведений системы управления версиями, и конкретное расположение в базе данных задается ProjName. Это поведение может вызывать проблемы после ветви, разветвление или операций копирования, так как ProjName обычно будет недопустимым после любой из этих операций.  
  
 В API подключаемых модулей управления исходной версии 1.1, интегрированной среды разработки используется ~ SAK-файлов для обнаружения, если подключаемый модуль поддерживается MSSCCPRJ. Метод SCC хранения информация системы управления версиями. API подключаемых модулей управления исходной версии 1.2 предоставляет новую возможность для обнаружения поддержка MSSCCPRJ. Файл SCC без использования ~ SAK-файл. Дополнительные сведения см. в разделе [Устранение ~ SAK-файлов](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>См. также  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
