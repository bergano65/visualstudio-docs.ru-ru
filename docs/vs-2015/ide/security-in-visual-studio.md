---
title: Безопасность в Visual Studio | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5952b42426f09a0f6e3bcdb6faf318774165f587
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557781"
---
# <a name="security-in-visual-studio"></a>Безопасность в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [безопасность в Visual Studio](https://docs.microsoft.com/visualstudio/ide/security-in-visual-studio).  
  
Вопросы безопасности должны рассматриваться на всех этапах разработки приложения — от проектирования до развертывания. Начните работу с запуска Visual Studio в наиболее безопасном режиме. См. раздел [Разрешения пользователей](../ide/user-permissions-and-visual-studio.md).  
  
 Для успешной разработки безопасного приложения следует ознакомиться с основными понятиями безопасности и средствами защиты платформ, для которых разрабатывается приложение. Кроме того, необходимо понимать приемы безопасного кодирования.  
  
## <a name="understanding-security"></a>Общее представление о безопасности  
 [Безопасность](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)  
 Описание управления доступом к коду, ролевой политики безопасности, а также политики и средств безопасности в .NET Framework.  
  
 [Десять советов по защите кода, которые должен знать каждый разработчик](http://go.microsoft.com/fwlink/?LinkId=72877)  
 Вопросы, внимание к которым позволит избежать возникновения угрозы безопасности для данных или системы.  
  
## <a name="coding-for-security"></a>Безопасное кодирование  
 Большинство ошибок кодирования, которые приводят к уязвимости системы безопасности, происходит из-за неправильных допущений разработчиков при работе с вводимыми пользователем данными или из-за неполного понимания принципов работы платформы, для которой разрабатывается приложение.  
  
 [Правила написания безопасного кода](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)  
 Правила классификации компонентов для решения вопросов безопасности.  
  
 [Рекомендации по безопасности](http://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42)  
 Описание переполнения буфера и общая картина функциональности проверки безопасности в Microsoft Visual C++, которая включается с помощью флага времени компиляции /GS.



