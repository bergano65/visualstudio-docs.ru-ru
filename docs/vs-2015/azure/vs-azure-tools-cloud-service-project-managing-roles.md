---
title: Управление ролями в облачных службах Azure с помощью Visual Studio | Документация Майкрософт
description: Узнайте, как добавлять и удалять роли в облачных службах Azure с помощью Visual Studio.
author: ghogen
manager: douge
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 35221cbf98f26a71e2b4adf0a7178342616ff7c0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002887"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Управление ролями в облачных службах Azure с помощью Visual Studio
После создания облачной службы Azure, можно добавить в него новые роли или удалить из него существующие роли. Также можно импортировать существующий проект и преобразовать его в роль. Например можно импортировать веб-приложения ASP.NET и назначают его веб-роли.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Добавление роли облачной службы Azure
Следующие шаги описывают Добавление рабочей или веб-роли в проект Azure облачной службы в Visual Studio.

1. Создайте или откройте проект облачной службы Azure в Visual Studio.

1. В **обозревателе решений**, разверните узел проекта

1. Щелкните правой кнопкой мыши **роли** для отображения в контекстном меню узла. В контекстном меню выберите **добавить**, затем выберите существующий веб-роли или рабочей роли из текущего решения или создать проект рабочей или веб-роли. Кроме того, можно также выбрать проект, например проекта веб-приложения ASP.NET и связать его с проектом роли.

    ![Параметры меню для добавления роли проекта облачной службы](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Удаление роли из облачной службы Azure
Следующие шаги описывают удаление рабочей или веб-роли из проекта облачной службы Azure в Visual Studio.

1. Создайте или откройте проект облачной службы Azure в Visual Studio.

1. В **обозревателе решений**, разверните узел проекта

1. Разверните **ролей** узла.

1. Щелкните правой кнопкой мыши узел, который требуется удалить и в контекстном меню выберите **удалить**. 

    ![Параметры меню для добавления роли облачной службы Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Повторное добавление роли в проект облачной службы Azure
Если вы удалите роль из проекта облачной службы, но в дальнейшем захочет добавить роль в проект, добавляются только декларация роли и ее основные атрибуты, такие как конечные точки и диагностики. Никакие дополнительные ресурсы или ссылки, добавляемые `ServiceDefinition.csdef` файл или `ServiceConfiguration.cscfg` файл. Если вы хотите добавить эту информацию, необходимо вручную добавить его обратно в эти файлы.

Например можно удалить веб-службы роли, и позднее вы решите добавить эту роль обратно в ваше решение. Если в этом случае возникает ошибка. Чтобы предотвратить эту ошибку, необходимо добавить `<LocalResources>` элемент, показанный в следующем XML обратно в `ServiceDefinition.csdef` файл. Используйте имя роли веб-службы, которую вы добавили обратно в проект как часть атрибута имени **<LocalStorage>** элемент. В этом примере имя роли веб-службы является **WCFServiceWebRole1**.

    <WebRole name="WCFServiceWebRole1">
        <Sites>
          <Site name="Web">
            <Bindings>
              <Binding name="Endpoint1" endpointName="Endpoint1" />
            </Bindings>
          </Site>
        </Sites>
        <Endpoints>
          <InputEndpoint name="Endpoint1" protocol="http" port="80" />
        </Endpoints>
        <Imports>
          <Import moduleName="Diagnostics" />
        </Imports>
       <LocalResources>
          <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
       </LocalResources>
    </WebRole>

## <a name="next-steps"></a>Следующие шаги
- [Настройка ролей для облачной службы Azure с помощью Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
