---
title: Развертывание приложений ClickOnce для тестирования и рабочих серверов без повторного подписывания | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b4761ed7f0b223e459fc1ac77ad93c546e02dc
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2018
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Развертывание приложений ClickOnce для тестовых и рабочих серверов без повторного подписывания
В этой статье рассматриваются функции ClickOnce, введенная в платформе .NET Framework версии 3.5, которая обеспечивает возможность развертывания приложений ClickOnce из нескольких сетевых расположений без повторного подписывания ClickOnce или манифесты.  
  
> [!NOTE]
>  Повторного подписывания по-прежнему является предпочтительным для развертывания новых версий приложений. По возможности используйте метод подписания заново. Дополнительные сведения см. в разделе [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Сторонние разработчики и независимые поставщики программного обеспечения можно включить эту функцию, облегчая для своих клиентов процедуру обновления своих приложений. Эта функция может использоваться в следующих ситуациях:  
  
-   При обновлении приложения, не при первой установке приложения.  
  
-   Если имеется только одна конфигурация приложения на компьютере. Например если приложение настроено на двух разных базах данных, нельзя использовать эту функцию.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Исключение deploymentProvider из манифесты развертывания  
 В .NET Framework 2.0 и .NET Framework 3.0, необходимо перечислить все приложения ClickOnce, которое устанавливается в системе для доступности в автономном режиме `deploymentProvider` в своем манифесте развертывания. `deploymentProvider` Часто называется расположение обновлений; это расположение, где ClickOnce проверяет наличие обновлений приложения. Это требование, а также необходимость издателей приложений подписывать их развертывания затрудняет для компании обновление приложения ClickOnce от поставщика или сторонних разработчиков. Он также позволяет усложнить для развертывания одного приложения из нескольких мест в одной сети.  
  
 С учетом изменений, внесенных в ClickOnce в .NET Framework 3.5 то возможна сторонних производителей для обеспечения приложение ClickOnce другой организации, который затем можно развернуть приложение на основе собственной сети.  
  
 Чтобы воспользоваться этой функцией, необходимо исключить разработчики приложений ClickOnce `deploymentProvider` из их развертывания манифесты. Это требование означает, что необходимо исключить `-providerUrl` манифесты аргумент при создании развертывания с помощью Mage.exe. Или, при создании манифестов развертывания в MageUI.exe, необходимо проверить, **место запуска** текстовое поле в **манифест приложения** вкладку остается пустым.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider и обновления приложений.  
 Начиная с .NET Framework 3.5, больше не нужно указать `deploymentProvider` в манифесте развертывания для развертывания приложения ClickOnce для использования сети и вне сети. Это изменение поддерживает сценарий, где необходимо упаковать и подписать развертывание самостоятельно, но позволяет другие компании для развертывания приложения в своих сетях.  
  
 Важно помнить, что приложения, исключающие `deploymentProvider` нельзя изменять местоположение своей установки во время обновления, пока они поставляют обновление, которое включает `deploymentProvider` тег еще раз.  
  
 Ниже приведены два примера позволяет прояснить это утверждение. В первом примере публикация приложения ClickOnce, которое не имеет `deploymentProvider` тега и попросите пользователей установить его из http://www.adatum.com/MyApplication/. Если вы решите для публикации приложения из следующего обновления http://subdomain.adatum.com/MyApplication/, у вас нет возможности объекта обозначающая это в манифесте развертывания, который находится в http://www.adatum.com/MyApplication/. Необходимо выполнить одно из следующих действий:  
  
-   Попросите пользователей удалить предыдущую версию и установить новую версию из нового расположения.  
  
-   Включить обновление на http://www.adatum.com/MyApplication/ , включающего `deploymentProvider` команды http://www.adatum.com/MyApplication/. Отпустите другим обновлением позже с помощью `deploymentProvider` команды http://subdomain.adatum.com/MyApplication/.  
  
 Во втором примере публикация приложения ClickOnce, которое указывает `deploymentProvider`, а затем решили удалить его. Один раз новой версии без `deploymentProvider` загружается на клиенты, не может перенаправлять путь, используемый для обновления до выпуска версии приложения, которое имеет `deploymentProvider` восстановлена. Как и в первом примере `deploymentProvider` первоначально должен указывать на местоположение текущего обновления, а не на новое местоположение. В этом случае при попытке вставить `deploymentProvider` , обозначающий http://subdomain.adatum.com/MyApplication/, происходит сбой следующего обновления.  
  
## <a name="creating-a-deployment"></a>Создание развертывания  
 Пошаговое руководство по созданию развертываний, которые могут развертываться из разных мест сети см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce, Does не требуют Re-Signing и что сохраняет сведения об](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
## <a name="see-also"></a>См. также  
 [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (средство создания и редактирования манифестов, графический клиент)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)