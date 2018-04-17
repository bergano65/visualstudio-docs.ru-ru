---
title: Развертывание приложений ClickOnce для тестирования и рабочих серверов без повторного подписывания | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 54474f0388ecbdbc9b1b1cb207544fd7091c1e96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Развертывание приложений ClickOnce для тестовых и рабочих серверов без повторного подписывания
В этом разделе описывается новая функция представлена в .NET Framework версии 3.5, которая обеспечивает возможность развертывания приложений ClickOnce из нескольких сетевых расположений без повторного подписывания ClickOnce или манифесты ClickOnce.  
  
> [!NOTE]
>  Повторного подписывания по-прежнему является предпочтительным для развертывания новых версий приложений. По возможности используйте метод подписания заново. Дополнительные сведения см. в разделе [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Сторонние разработчики и независимые поставщики программного обеспечения можно согласиться на эту функцию, облегчая для своих клиентов процедуру обновления своих приложений. Эта функция может использоваться в следующих ситуациях:  
  
-   При обновлении приложения, не являющегося первой установкой приложения.  
  
-   Если имеется только одна конфигурация приложения на компьютере. Например если приложение настроено на двух разных базах данных, нельзя использовать эту функцию.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Исключение deploymentProvider из манифесты развертывания  
 В .NET Framework 2.0 и .NET Framework 3.0, необходимо указать все приложения ClickOnce, которое устанавливается в системе для доступности в автономном режиме `deploymentProvider` в своем манифесте развертывания. `deploymentProvider` Часто называется расположение обновлений; это расположение, в котором ClickOnce проверяет наличие обновлений приложения. Данное требование в сочетании с необходимостью для издателей приложений подписывать свои развертывания, затрудняет для компании обновление приложения ClickOnce от поставщика или другой сторонней компании. Он также позволяет усложнить для развертывания одного приложения из нескольких мест в одной сети.  
  
 С учетом изменений, внесенных в ClickOnce в .NET Framework 3.5 то возможна сторонних разработчиков для предоставления приложения ClickOnce для другой организации, которая затем можно развернуть приложение на основе собственной сети.  
  
 Чтобы воспользоваться этой функцией, необходимо исключить разработчики приложений ClickOnce `deploymentProvider` из их развертывания манифесты. Это означает исключение `-providerUrl` манифесты аргумент при создании развертывания с помощью Mage.exe или убедившись **место запуска** текстовое поле в **манифест приложения** вкладку оставлено пустым Если вы создании манифестов развертывания в MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider и обновления приложений.  
 Начиная с .NET Framework 3.5, больше не нужно указать `deploymentProvider` в манифесте развертывания для развертывания приложения ClickOnce для использования сети и вне сети. Это поддерживает сценарий, где необходимо упаковать и подписать развертывание самостоятельно, но позволяет другие компании для развертывания приложения в своих сетях.  
  
 Важно помнить это приложения, исключающие `deploymentProvider` нельзя изменять местоположение своей установки во время обновления, пока они поставляют обновление, которое включает `deploymentProvider` тег еще раз.  
  
 Ниже приведены два примера позволяет прояснить это утверждение. В первом примере публикация приложения ClickOnce, которое не имеет `deploymentProvider` тега и попросите пользователей установить его из http://www.adatum.com/MyApplication/. Если вы решите для публикации приложения из следующего обновления http://subdomain.adatum.com/MyApplication/, будет никак не могут это это означает в манифесте развертывания, который находится в http://www.adatum.com/MyApplication/. Необходимо выполнить одно из следующих действий:  
  
-   Попросите пользователей удалить предыдущую версию и установить новую версию из нового расположения.  
  
-   Включить обновление на http://www.adatum.com/MyApplication/ , включающего `deploymentProvider` команды http://www.adatum.com/MyApplication/. Отпустите другим обновлением позже с помощью `deploymentProvider` команды http://subdomain.adatum.com/MyApplication/.  
  
 Во втором примере публикация приложения ClickOnce, которое указывает `deploymentProvider`, а затем решили удалить его. Один раз новой версии без `deploymentProvider` был загружен для клиентов, можно не будет перенаправлять путь, используемый для обновления до выпуска версии приложения, которое имеет `deploymentProvider` восстановлена. Как и в первом примере `deploymentProvider` первоначально должен указывать на местоположение текущего обновления, а не на новое местоположение. В этом случае при попытке вставить `deploymentProvider` , обозначающий http://subdomain.adatum.com/MyApplication/, то произойдет сбой следующего обновления.  
  
## <a name="creating-a-deployment"></a>Создание развертывания  
 Пошаговое руководство по созданию развертываний, которые могут развертываться из разных мест сети см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce, Does не требуют Re-Signing и что сохраняет сведения об](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>См. также  
 [Mage.exe (средство создания и редактирования манифеста)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (средство создания и редактирования манифестов, графический клиент)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)