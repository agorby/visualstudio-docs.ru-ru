---
title: Идентификаторы для подписчиков Visual Studio
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: Как добавить альтернативный идентификатор для подписки Visual Studio, который будет использоваться для VSTS и Azure
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: vs subscription
ms.openlocfilehash: 9a83f78f35b9533c554c81cecd181c00eca05568
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Идентификаторы для подписчиков Visual Studio

Когда вы активируете подписку Visual Studio, мы привязываем ваш идентификатор (или имя пользователя), использованный при активации, к подписке Visual Studio. Таким образом, мы узнаем вас на [портале подписчиков Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), в Visual Studio Team Services (VSTS) и в Azure.

В VSTS мы проверяем состояние вашей подписки Visual Studio при каждом входе и автоматически предоставляем вам возможности каждой учетной записи, членом которой вы являетесь.
Поскольку эти возможности являются преимуществами подписчиков, вас можно бесплатно добавить в любую учетную запись VSTS с помощью идентификатора, привязанного к вашей подписке Visual Studio.

В Azure мы проверяем состояние вашей подписки Visual Studio при активации [ежемесячного кредита Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/), который является преимуществом подписчиков.

На [портале подписчиков Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) вы можете добавить **альтернативный идентификатор** — помимо идентификатора, использованного при активации. В настоящий момент вы можете добавить альтернативный идентификатор, если вы использовали учетную запись Майкрософт для активации подписки. Таким образом, вы можете добавить рабочую или учебную учетную запись (которую вы используете при входе в Visual Studio, Office 365, сеть организации или школы), чтобы использовать VSTS через личную учетную запись, а также рабочую или учебную учетную запись.

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>Добавление альтернативной учетной записи в подписку Visual Studio

Добавление альтернативной учетной записи в подписку Visual Studio позволяет получать доступ к преимуществам подписки, таким как Visual Studio Team Services (VSTS) и Azure, с идентификатором, отличным от того, которому назначена подписка. В прошлом эта возможность была доступна, только если подписка Visual Studio была назначена учетной записи Майкрософт. Мы распространили ее на рабочие и учебные учетные записи в Azure Active Directory (Azure AD).

При этом копия подписки не предоставляет другой учетной записи. Вы лишь получаете возможность доступа к указанным преимуществам с помощью альтернативной учетной записи.

Для всех подписок можно добавить рабочую или учебную учетную запись, чтобы использовать ее с преимуществами, требующими входа (IDE Visual Studio, VSTS и Azure).

### <a name="prerequisites"></a>Предварительные требования

* [Разрешения администратора коллекции проектов VSTS или владельца учетной записи](https://docs.microsoft.com/en-us/vsts/accounts/faq-add-delete-users#find-owner).

* Для использования альтернативной учетной записи подписка, связанная с вашей учетной записью, должна включать Visual Studio Team Services или Microsoft Azure.

> [!Note]
> Вы можете продолжать использовать преимущества подписки с альтернативным идентификатором, однако подписка будет по-прежнему связана с исходной учетной записью.

### <a name="add-the-alternate-account"></a>Добавление альтернативной учетной записи

1. Войдите в Visual Studio, используя учетную запись Майкрософт (https://{ваша_учетная_запись}.visualstudio.com).

2. Перейдите в раздел **Подписки**.

  ![Добавление альтернативной учетной записи имени — переход к разделу "Подписки" в Visual Studio](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. Щелкните ссылку **Добавить альтернативную учетную запись**.

  ![Щелкните "Добавить альтернативную учетную запись" ](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. Добавьте рабочую или учебную учетную запись.

  ![Добавление рабочей или учебной учетной записи](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Войдите в Visual Studio, используя рабочую или учебную учетную запись (https://{ваша_учетная_запись}.visualstudio.com).

  ![Использование рабочей или учебной учетной записи](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

  Альтернативная учетная запись будет добавлена в подписку Visual Studio, что позволит использовать оба идентификатора для доступа к преимуществам подписки, требующим входа с помощью альтернативной учетной записи (IDE, VSTS и Azure).

Дополнительные сведения о добавлении альтернативной учетной записи см. на странице [Мои вопросы и ответы по Visual Studio](https://www.visualstudio.com/my/myvsfaq#alternate).

## <a name="faq"></a>часто задаваемые вопросы

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>Вопрос. Почему VSTS не распознает меня как подписчика Visual Studio?
Ответ. Служба VSTS должна автоматически распознавать вашу подписку при входе с основным или альтернативным идентификатором. Если этого не происходит, попробуйте выполнить следующее.

* Убедитесь, что у вас есть активная подписка Visual Studio, которая [включает VSTS в качестве преимущества](vs-vsts.md).

* Убедитесь, что выполнили вход с основным или альтернативным идентификатором для вашей подписки Visual Studio.

* Посетите [портал подписчиков Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) по крайней мере один раз перед входом в VSTS.

Если VSTS по-прежнему не распознает вашу подписку, [обратитесь в службу поддержки](https://www.visualstudio.com/team-services/support/)
