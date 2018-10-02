---
title: Развертывание приложений ClickOnce для тестовых и рабочих серверов без повторного подписывания | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 384292be2f08eef453dba5623783ef8865107d54
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571719"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Развертывание приложений ClickOnce для тестовых и рабочих серверов без повторного подписывания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [развертывание ClickOnce приложений для тестирования и рабочих серверов без Resigning](https://docs.microsoft.com/visualstudio/deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning).  
  
В этом разделе описана новая функция ClickOnce, введенная в .NET Framework версии 3.5, которая включает развертывание приложений ClickOnce из нескольких мест сети без повторного подписывания приложения ClickOnce или манифесты.  
  
> [!NOTE]
>  Повторного подписывания по-прежнему является предпочтительным для развертывания новых версий приложений. По возможности используйте метод подписания заново. Дополнительные сведения см. в разделе [Mage.exe (средство создания и редактирования манифеста)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Сторонних разработчиков и независимых поставщиков программного обеспечения можно согласиться на эту функцию, что облегчает пользователям обновлять свои приложения. Эта функция может использоваться в следующих ситуациях:  
  
-   При обновлении приложения, не первой установки приложения.  
  
-   Если имеется только одна конфигурация приложения на компьютере. Например если приложение настроено для указания двух разных базах данных, нельзя использовать эту функцию.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Исключение deploymentProvider из манифесты развертывания  
 В .NET Framework 2.0 и .NET Framework 3.0, необходимо указать любое приложение, которое устанавливается в системе для доступности в автономном режиме `deploymentProvider` в своем манифесте развертывания. `deploymentProvider` Часто называется расположение обновлений; это расположение, в котором ClickOnce будет проверять наличие обновлений приложения. Это требование, в сочетании с необходимостью для издателей приложений подписывать свои развертывания, затрудняет для компании обновление от поставщика или других сторонних приложений ClickOnce. Она также усложняет развертывание одного приложения из нескольких расположений в той же сети.  
  
 С помощью изменений, внесенных в ClickOnce в .NET Framework 3.5 можно для независимых производителей, обеспечивая приложений ClickOnce в другую организацию, которой затем можно развернуть приложение в своей собственной сети.  
  
 Чтобы воспользоваться преимуществами этой функции, разработчики приложений ClickOnce необходимо исключить `deploymentProvider` из их развертывание манифестов. Это означает исключение `-providerUrl` аргумент при создании развертывания манифестов с помощью Mage.exe или обеспечение **место запуска** текстовое поле в **манифест приложения** вкладке оставлено пустым Если вы создается манифесты развертывания в MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider обновлений и приложений  
 Начиная с .NET Framework 3.5, вы больше не нужно указывать `deploymentProvider` в манифесте развертывания для развертывания ClickOnce-приложения для использования сетевой и автономный режим. Поддерживает сценарий, где необходимо упаковать и подписать развертывание самостоятельно, но разрешить другие компании для развертывания приложения в их сетях.  
  
 Главное помнить является то, что приложения, исключающие `deploymentProvider` нельзя изменять местоположение своей установки во время обновления, пока они поставляют обновление, которое содержит `deploymentProvider` тег еще раз.  
  
 Ниже приведены два примера позволяет прояснить это. В первом примере, публикации приложения ClickOnce, который не имеет `deploymentProvider` тег и попросите пользователей установить его из http://www.adatum.com/MyApplication/. Если вы решите опубликовать следующего обновления приложения от http://subdomain.adatum.com/MyApplication/, вы не сможете из означающую, что это в манифесте развертывания, который находится в http://www.adatum.com/MyApplication/. Необходимо выполнить одно из следующих действий:  
  
-   Попросите пользователей удалить предыдущую версию и установить новую версию из нового расположения.  
  
-   Включить обновление на http://www.adatum.com/MyApplication/ , включающий `deploymentProvider` указывает на http://www.adatum.com/MyApplication/. Отпустите другим обновлением позже с помощью `deploymentProvider` указывает на http://subdomain.adatum.com/MyApplication/.  
  
 Во втором примере, публикации приложения ClickOnce, указывающее `deploymentProvider`, а затем решили удалить ее. Один раз в новую версию без `deploymentProvider` загрузки на клиентах, не можно перенаправлять путь, используемый для обновления, пока не будет выпущена версия вашего приложения, которое имеет `deploymentProvider` восстановлена. Как и в первом примере `deploymentProvider` изначально должен указывать на местоположение текущего обновления, а не на новое местоположение. В данном случае, если попытаться вставить `deploymentProvider` , ссылающийся на http://subdomain.adatum.com/MyApplication/, то произойдет сбой следующего обновления.  
  
## <a name="creating-a-deployment"></a>Создание развертывания  
 Пошаговое руководство по созданию развертываний, которые могут быть развернуты из разных мест сети, см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce, Does не требуют Re-Signing и что сохраняет сведения об](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>См. также  
 [Mage.exe (средство создания и редактирования манифеста)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (средство создания и редактирования манифестов, графический клиент)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)



