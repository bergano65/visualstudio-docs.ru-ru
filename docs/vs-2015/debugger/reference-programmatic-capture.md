---
title: Справочник (программный захват) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c68b196829b1ecf27732e325c6d2b402c720c94
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230351"
---
# <a name="reference-programmatic-capture"></a>Справочник (программный захват)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Диагностика графики поддерживает управление функциями записи через API программного захвата. Этот API можно использовать для переключения и добавления сообщений на головной дисплей, инициализации и создания файлов журнала графики, а также для захвата графических данных.  
  
## <a name="programmatic-capture-apis"></a>API программного захвата  
  
### <a name="classes"></a>Классы  
  
|Имя|Описание|  
|----------|-----------------|  
|[Класс VsgDbg](../debugger/vsgdbg-class.md)|Представляет интерфейс для программного управления компонентом диагностики графики в приложении.|  
  
### <a name="preprocessor-symbols"></a>Символы препроцессора  
  
|name|Описание|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Определяет своим наличием, нужно ли сохранять файл журнала графики в каталог временных файлов пользователя.|  
|[VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)|Определяет имя файла журнала графики по умолчанию.|  
|[VSG_NODEFAULT_INSTANCE](../debugger/vsg-nodefault-instance.md)|Определяет своим наличием, нужно ли предоставлять экземпляр класса `VsgDbg` по умолчанию.|  
  
## <a name="related-articles"></a>Связанные статьи  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Capturing Graphics Information](../debugger/capturing-graphics-information.md)|Показывает, как захватывать графическую информацию из приложения DirectX для использования инструментов диагностики графики [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], помогающих выявлять проблемы отрисовки.|  
|[Обзор набора средств Visual Studio для Unity](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Показывает, каким образом диагностика графики помогает отлаживать ошибки отрисовки в играх и приложениях DirectX.|



