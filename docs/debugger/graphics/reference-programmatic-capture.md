---
title: Справочник (программный захват) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 892831423ccc3607db1b3f162fb79f4508764afa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006755"
---
# <a name="reference-programmatic-capture"></a>Справочник (программный захват)
Диагностика графики поддерживает управление функциями записи через API программного захвата. Этот API можно использовать для переключения и добавления сообщений на головной дисплей, инициализации и создания файлов журнала графики, а также для захвата графических данных.  

## <a name="programmatic-capture-apis"></a>API программного захвата  

### <a name="classes"></a>Классы  

|name|Описание|  
|----------|-----------------|  
|[Класс VsgDbg](vsgdbg-class.md)|Представляет интерфейс для программного управления компонентом диагностики графики в приложении.|  

### <a name="preprocessor-symbols"></a>Символы препроцессора  

|name|Описание|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Определяет своим наличием, нужно ли сохранять файл журнала графики в каталог временных файлов пользователя.|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Определяет имя файла журнала графики по умолчанию.|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Определяет своим наличием, нужно ли предоставлять экземпляр класса `VsgDbg` по умолчанию.|  

## <a name="related-articles"></a>Связанные статьи  

| Заголовок | Описание |
| - | - |
| [Capturing Graphics Information](capturing-graphics-information.md) | Показывает, как захватывать графическую информацию из приложения DirectX для использования инструментов диагностики графики [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], помогающих выявлять проблемы отрисовки. |
| [Обзор](overview-of-visual-studio-graphics-diagnostics.md) | Показывает, каким образом диагностика графики помогает отлаживать ошибки отрисовки в играх и приложениях DirectX. |
