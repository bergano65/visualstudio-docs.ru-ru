---
title: Справочник (программный захват) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cebeb7eb651c11b5f560b981df30213fc726c66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989785"
---
# <a name="reference-programmatic-capture"></a>Справочник (программный захват)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Диагностика графики поддерживает управление функциями записи через API программного захвата. Этот API можно использовать для переключения и добавления сообщений на головной дисплей, инициализации и создания файлов журнала графики, а также для захвата графических данных.  
  
## <a name="programmatic-capture-apis"></a>API программного захвата  
  
### <a name="classes"></a>Классы  
  
|name|Описание|  
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
|[Обзор](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Показывает, каким образом диагностика графики помогает отлаживать ошибки отрисовки в играх и приложениях DirectX.|
