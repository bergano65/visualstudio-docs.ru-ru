---
title: "Безопасность в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 8e34062596ab2f87ae97934b89b4c292e8f28f32
ms.lasthandoff: 02/22/2017

---
# <a name="security-in-visual-studio"></a>Безопасность в Visual Studio
Вопросы безопасности должны рассматриваться на всех этапах разработки приложения — от проектирования до развертывания. Начните работу с запуска Visual Studio в наиболее безопасном режиме. См. раздел [Разрешения пользователей](../ide/user-permissions-and-visual-studio.md).  
  
 Для успешной разработки безопасного приложения следует ознакомиться с основными понятиями безопасности и средствами защиты платформ, для которых разрабатывается приложение. Кроме того, необходимо понимать приемы безопасного кодирования.  
  
## <a name="understanding-security"></a>Общее представление о безопасности  
 [Безопасность](http://msdn.microsoft.com/Library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)  
 Описание управления доступом к коду, ролевой политики безопасности, а также политики и средств безопасности в .NET Framework.  
  
 [Десять советов по защите кода, которые должен знать каждый разработчик](http://go.microsoft.com/fwlink/?LinkId=72877)  
 Вопросы, внимание к которым позволит избежать возникновения угрозы безопасности для данных или системы.  
  
## <a name="coding-for-security"></a>Безопасное кодирование  
 Большинство ошибок кодирования, которые приводят к уязвимости системы безопасности, происходит из-за неправильных допущений разработчиков при работе с вводимыми пользователем данными или из-за неполного понимания принципов работы платформы, для которой разрабатывается приложение.  
  
 [Правила написания безопасного кода](http://msdn.microsoft.com/Library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)  
 Правила классификации компонентов для решения вопросов безопасности.  
  
 [Рекомендации по безопасности](/visual-cpp/top/security-best-practices-for-cpp)  
 Описание переполнения буфера и общая картина функциональности проверки безопасности в Microsoft Visual C++, которая включается с помощью флага времени компиляции /GS.
