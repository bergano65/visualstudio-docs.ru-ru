---
title: начало работы с расширяемостью отладчика | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152710"
---
# <a name="getting-started-with-debugger-extensibility"></a>Приступая к работе с расширением отладчика
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Предоставляет сведения, которые необходимы для создания и настройки компонентов отладчика, используемых для отладки программ в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среде.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в отладке добавлены улучшения, полученные в результате расширенного тестирования удобства использования, выполненного на предыдущих [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладчиках. Можно использовать [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладку для пошагового выполнения многоязыкового приложения. также можно реализовать Оперативное редактирование переменных во время отладки приложений и решений на разных языках.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладка выполняется вне процесса с отлаживаемой программой и, таким образом, менее агрессивна в пространстве процесса приложения. Следовательно, проще писать компоненты, взаимодействующие с отладчиком, не влияя на программу отладки.  
  
 Для лучшего использования необходимо [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] иметь представление о следующих возможностях:  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Интегрированная среда разработки (IDE)  
  
- Язык программирования C++  
  
- ATL COM  
  
## <a name="in-this-section"></a>в этом разделе  
 [Схема для расширения отладчика](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Описывает процесс реализации отладки в продукте в зависимости от компилятора и его выходных данных.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Содержит общие сведения о [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] компонентах отладки, включая модуль отладки (de), средство оценки выражений (EE) и обработчик символов (SH).  
  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные понятия архитектуры отладки.  
  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как подсистема отладки (DE) работает одновременно в рамках кода, документации и контекстов оценки выражений. Описывает, что касается каждого из трех контекстов: расположение, положение или вычисление, относящиеся к нему.  
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, такие как запуск программы и вычисление выражений.
