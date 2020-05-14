---
title: Развертывание приложений ClickOnce без повторной подписи
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395326"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Развертывание clickOnce приложений для тестирования и производства серверов без отказа
В этой статье описывается функция ClickOnce, представленная в версии 3.net Framework 3.5, которая позволяет развертывать приложения ClickOnce из нескольких сетевых точек без повторного подписания или изменения манифестов ClickOnce.

> [!NOTE]
> Отказ от этого по-прежнему является предпочтительным методом развертывания новых версий приложений. По возможности используйте метод отставки. Дополнительные сведения см. в разделе [*Mage.exe* (инструмент создания и изменения манифестов)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Сторонние разработчики и ISV могут выбрать эту функцию, что упрощает обновление их приложений для их клиентов. Эта функция может быть использована в следующих ситуациях:

- При обновлении приложения не при первой установке приложения.

- При наличии только одной конфигурации приложения на компьютере. Например, если приложение настроено для уточки на две разные базы данных, эту функцию использовать нельзя.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Исключить развертываниеProvider из манифестов развертывания
 В .NET Framework 2.0 и .NET Framework 3.0 любое приложение ClickOnce, которое устанавливается в систему для доступности в автономном режиме, должно уотедать `deploymentProvider` в манифесте развертывания. Часто `deploymentProvider` упоминается как расположение обновления; это место, где ClickOnce проверяет обновления приложений. Это требование, наряду с необходимостью для издателей приложений подписать свои развертывания, затруднив для компании обновление приложения ClickOnce от поставщика или другой третьей стороны. Это также затрудняет развертывание одного и того же приложения из нескольких мест в одной сети.

 С изменениями, которые были внесены в ClickOnce в .NET Framework 3.5, это возможно для третьей стороны, чтобы предоставить приложение ClickOnce к другой организации, которая затем может развернуть приложение на своей собственной сети.

 Для того, чтобы воспользоваться этой функцией, `deploymentProvider` разработчики приложений ClickOnce должны исключить из своих манифестов развертывания. Это требование означает, что `-providerUrl` при создании манифестов развертывания с Mage.exe необходимо исключить аргумент при создании манифестов развертывания. Или, если вы генерируете манифесты развертывания с MageUI.exe, вы должны убедиться, что текстовый ящик **местоположения запуска** на вкладке **Application Manifest** остается пустым.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider и обновления приложений
 Начиная с .NET Framework 3.5, вам больше `deploymentProvider` не нужно указывать в манифесте развертывания, чтобы развернуть приложение ClickOnce как для онлайн, так и для автономного использования. Это изменение поддерживает сценарий, в котором необходимо упаковать и подписать развертывание самостоятельно, но позволяет другим компаниям развертывать приложение в своих сетях.

 Важно помнить, что приложения, которые `deploymentProvider` исключают не может изменить свое местоположение установки `deploymentProvider` во время обновления, пока они не отправят обновление, которое включает тег снова.

 Вот два примера, чтобы прояснить этот момент. В первом примере вы публикуете приложение `deploymentProvider` ClickOnce, которое не имеет `http://www.adatum.com/MyApplication/`тега, и просите пользователей установить его из. Если вы решите опубликовать следующее обновление `http://subdomain.adatum.com/MyApplication/`приложения из, у вас нет способа обозначить `http://www.adatum.com/MyApplication/`это в манифесте развертывания, который находится в . Вы можете сделать одну из двух вещей:

- Покажите пользователям удалить предыдущую версию и установить новую версию из нового местоположения.

- Включите `http://www.adatum.com/MyApplication/` обновление о `deploymentProvider` том, что включает в себя указывая на `http://www.adatum.com/MyApplication/`. Затем выпустите `deploymentProvider` еще `http://subdomain.adatum.com/MyApplication/`одно обновление позже с указанием на .

  Во втором примере вы публикуете приложение ClickOnce, которое `deploymentProvider`определяет, и затем вы решаете удалить его. После того, `deploymentProvider` как новая версия без загружается клиентам, вы не можете перенаправить `deploymentProvider` путь, используемый для обновления, пока вы не выпустите версию приложения, которая была восстановлена. Как и в `deploymentProvider` первом примере, сначала следует указать на текущее местоположение обновления, а не на новое местоположение. В этом случае, если вы `deploymentProvider` попытаетесь вставить, что относится к `http://subdomain.adatum.com/MyApplication/`, то следующее обновление не удается.

## <a name="create-a-deployment"></a>Создание развертывания
 Для шаг за шагом руководства по созданию развертываний, которые могут быть развернуты из разных сетевых местоположений, [см. Walkthrough: Ручно развертывайте приложение ClickOnce, которое не требует повторной подписи и которое сохраняет информацию](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)о брендинге.

## <a name="see-also"></a>См. также
- [*Mage.exe* (Manifest Поколения и Редактирование инструмент)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Manifest Поколения и Редактирование инструмент, графический клиент)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
