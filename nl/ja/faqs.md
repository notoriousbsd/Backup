---

copyright:
  years: 1994, 2018
lastupdated: "2018-12-14"

---
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}


# FAQ

## どのような種類のアプリケーションをバックアップできますか。
{: faq}

{{site.data.keyword.backup_full}} では、さまざまなアプリケーションをバックアップできます。 ただし、{{site.data.keyword.BluSoftlayer_full}} では、バックアップ対象のより一般的な一部のソフトウェア・システム用に、次を含むソフトウェア・エージェントが提供されます。

- ベアメタルのリストア
- Microsoft Exchange
- Microsoft SQL
- Oracle

ここにリストされているプラグインは Windows サーバーとのみ互換性があります (Oracle プラグインは例外)。 各エージェントは、ご使用のバックアップ・サービスに対するアドオンとして使用可能です。 エージェントをサービスに追加するには、営業チームのメンバーに今すぐご連絡ください。

<hr>

## どの程度の頻度でデータをバックアップできますか。
{: faq}

WebCC では、バックアップを手動で作成することも、単一インスタンスとして、または繰り返し実行されるバックアップをスケジュールすることもできます。 繰り返し実行されるバックアップは、日次、週次、月次、またはカスタム・スケジュールで作成でき、いつでも更新したり取り消したりできます。

毎日または毎時に複数回実行される高頻度のバックアップにより、バックアップ・ジョブが破損する可能性があります。 この破損は、バックアップ・ボールトにおいて、必要なバックグラウンド保守作業を実行するための十分の時間がないために発生します。バックアップ・ジョブは、保守作業より優先して実行されます。そのため、高い頻度でバックアップを行うと、ボールトはバックアップ・ジョブを実行し続けるので、セーフセットの数が増大します。
{:note}

<hr>

## 保存方式はどのように機能しますか。
{: faq}

{{site.data.keyword.backup_notm}} では、ロールバックを必要とする期間に応じたデータ保存が可能です。 **日次**保存方式の場合、データは 7 日間保存されますが、**週次**方式の場合は 1 カ月間保持され、**月次**方式の場合は 1 年間保持されます。 各期間の終了時には、最も古いデータ・セットが置き換えられ、最初に作成された「差分バックアップ」が、使用可能な最も古いリストア・ポイントになります。

デフォルトの保存方式を変更することもできますし、カスタム保存方式を作成することもできます。とはいえ、開始点としては、デフォルトの保存方式を使用することを推奨します。新規保存スキームを作成したり既存の保存方式を変更したりするには、「アーカイブ (Archiving)」オプションのチェック・マークを外してください。アーカイブはサポートされていません。
{:tip}

<hr>

## 差分テクノロジーとは何ですか。
{: faq}

最初のバックアップは「シード」(完全なフルバックアップ) であり、次以降のバックアップは「差分」(つまり変更のみ) となりますが、これらは「フルバックアップ」と同等であり、フルバックアップと見なされます。 つまり、バックアップからすべてまたは任意のファイルをリストアできます。 このテクノロジーではセッションのたびに「フルバックアップ」を作成できますが、ボールト上の大量のスペースが節約され、後続の各バックアップを完了するためにかかる時間が短縮されます。

<hr>

## バックアップは保護されていますか?
{: faq}

デフォルトでは、通信回線上 (OTW) のすべての暗号化は AES 256 ビット暗号化を使用して行われます。 AES 256 ビットを使用する暗号化形式で、データを保管することも選択できます。

暗号化パスワードを忘れないようにしてください。 パスワードがないと、データをリストアできません。 パスワードを紛失した場合は、データを元に戻せなくなります。
{:important}

ゼロ圧縮から最大比率の圧縮までの圧縮率を使用でき、ファイル・タイプに応じて 20 % から 30 % の範囲で圧縮できます。

<hr>

## システム状態のバックアップで保管される情報は何ですか?
{: faq}

システム状態のバックアップには、COM + クラス登録データベース、レジストリー、ブート・ファイル、システム・ファイル、パフォーマンス・カウンターが含まれますが、これらに限定されません。 システムに完全に依存します。 システム・ファイルは、システム O/S とサービス・パックによって異なります。通常、何千ものシステム・ファイルが存在します。MS Windows では、バックアップにこれらの DLL を含める場合、その動的なリストが作成されます。システム・ファイルを含めることで、システム・ファイルが破損した場合、一部のサービス・パックを誤ってアンインストールした場合、ベアメタルのリストアでリカバリーする必要がある場合に、リカバリーが可能になります。 インストール・キットから O/S を再インストールして各サービス・パックを個別にインストールしなくても、バックアップの状態に戻ることができます。

システム状態のバックアップには、ユーザー・データ・ファイルは含まれません。 システム状態のバックアップ・ジョブは、スタンドアロン・ジョブとして構成する必要があります。 システム状態のバックアップ・ジョブにはその他のデータ・ソースが含まれていてはなりません。
{:important}

<hr>

## オープン・ファイルはどのように処理されますか。
{: faq}

デフォルトで、ベース・クライアントには、OS 上で実行中のほとんどのオープン・ファイルを処理する最先端のテクノロジーが備わっています。

<hr>

## 価格に関する情報はどこで確認できますか。
{: faq}

詳しくは、[Backup storage](https://www.ibm.com/cloud/backup-and-restore){:new_window} および [{{site.data.keyword.backup_notm}} on IBM Cloud: Pricing](https://www.ibm.com/cloud/evault/pricing){:new_window} を参照してください。

<hr>

## バックアップを危険にさらさずに {{site.data.keyword.backup_notm}} 容量を増減できますか?
{: faq}

[{{site.data.keyword.slportal}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com/){:new_window} でボールトのサイズを増減できます。 容量を変更しても、ボールトに保管されているデータの整合性には影響しません。 詳しくは、「[容量の拡大](expanding-capacity.html)」を参照してください。

<hr>

## {{site.data.keyword.backup_notm}} 容量を超えるとどうなりますか?
{: faq}

以前に購入した容量の制限に達した場合でも、バックアップを保存、取得できます。 ただし、請求書では、使用した追加の GB に関して追加課金されることに注意なさってください。

<hr>

## バックアップが失敗した場合に WebCC で通知を受けるよう、どのように設定できますか?
{: faq}

通知は「拡張 (Advanced)」タブで設定できます。 WebCC の**クイック・リンク**に示されている指示に従ってください。
