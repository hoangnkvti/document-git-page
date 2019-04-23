# 基本情報

## 概要

条件を指示して請求者の基本情報を検索できます。

## 条件
　[1. ID](#id)<br>
　[2. 郵便番号](#yubin)<br>
　[3. 氏名](#name)<br>
　[4. 電話／携帯](#tel)<br>
　[5. 性別](#sex)<br>
　[6. 在籍区分](#kubun)<br>
　[7. 卒業年](#sotsunen)<br>
　[8. 登録日](#baitdate)<br>
　[9. 住所文字列](#address)<br>
　[10. 都道府県](#ken)<br>
　[11. 地区](#chiku)<br>
　[12. 高校](#koko)<br>
　[13. 予備校](#yobiko)<br>
　[14. 高校](#koko)<br>
　[15. メール](#mail)<br>
　[16. メール有無](#mail_option)<br>
　[17. 誕生日](#birth)<br>
　[18. 例](#example)<br>

<hr>
<a name="id"/>

### ID

|Tên param|Database tương ứng|Loại data|Ý nghĩa|Ghi chú|
|-------|----------|-------|----------|----------|
|`j_id`|mast.id|array|Search bằng exact match(match toàn bộ ký tự) <br>Có thể search nhiều Id bằng cách thêm ký tự xuống dòng||

<hr>
<a name="yubin"/>

### 郵便番号
 (Số bưu điện)

|Tên param|Database tương ứng|Loại data|Ý nghĩa|Ghi chú|
|-------|----------|-------|----------|----------|
|`j_yubin`|mast.yubin|string|Match theo prefix|* Khi search thì xóa toàn bộ các ký tự khác số|

<hr>
<a name="name"/>

### 氏名
(Tên)

|Tên param|Database tương ứng|Loại data|Ý nghĩa|Ghi chú|
|-------|----------|-------|----------|----------|
|`j_sei`|mast.kanasei, mast.kanjisei|string|Default:Search theo Partial match|Không phân biệt Hiragana và Katakana|
|`j_mei`|mast.kanasei, mast.kanjisei|string|Default:Search theo Partial match|Không phân biệt Hiragana và Katakana|
|`j_type_sei`||array(1)|完全一致検索（無・有）|Khi check thì sẽ search theo Exact match|
|`j_type_mei`||array(1)|完全一致検索（無・有）|Khi check thì sẽ search theo Exact match|

<hr>
<a name="tel"/>

### 電話／携帯
(Số điện thoại)

|Tên param|Database tương ứng|Loại data|Ý nghĩa|Ghi chú|
|-------|----------|-------|----------|----------|
|`j_tel`|mast.tel, mast.keitai|string|Search theo partial match|Search bởi số đt hoặc số đt di động<br>* Bỏ qua tất cả những ký tự ngoài số|

<hr>
<a name="sex"/>

### 性別
(giới tính)

|Tên param|Database tương ứng|Loại data|Ý nghĩa|Ghi chú|
|-------|----------|-------|----------|----------|
|`j_sex`|mast.sex|array(3)|Search theo giá trị|mast.sex: 男=1, 女=2, 不明=0|

<hr>
<a name="kubun"/>

### 在籍区分

|Tên param|Database tương ứng|Loại data|Ý nghĩa|Ghi chú|
|-------|----------|-------|----------|----------|
|`j_kubun`|mast.kubun|array(13)|Search theo giá trị|mast.kubun: 高校生→その他：1→13|

<hr>
<a name="sotsunen"/>

### 卒業年
(năm tốt nghiệp)

|Tên param|Database tương ứng|Loại data|Ý nghĩa|Ghi chú|
|-------|----------|-------|----------|----------|
|`j_sotsunen`|mast.sotsunen|array(6)|Search theo giá trị|mast.sotsunen:<br>- 既卒(2018年以前): 2018<br>- 2019年→2002年: 2019→2022<br>- 2022年以降:2022<br>- 不明: 0|

<hr>
<a name="baitdate"/>

### 登録日
(Ngày đăng ký)

|Tên param|Database tương ứng|Loại data|Ý nghĩa|Ghi chú|
|-------|----------|-------|----------|----------|
|`j_baitdate_option`||int (1または2)|「最新請求」hoặc「初回請求」|最新請求: đăng ký mới nhất <br> 初回請求: đăng ký lần đầu <br> có case sẽ có nhiều data ở bảng Bait。(1)
|`j_baitdate_f`|bait.baitdate|date|Search từ ngày đc nhập|
|`j_baitdate_t`|bait.baitdate|date|Search đến ngày đc nhập|

*(1) Ví dụ、Bait data của mast có id=100001: có 3 records: baitdate=2018-01-01, 2018-02-01, 2018-03-01 -> 最新請求 là 2018-03-01、初回請求là 2018-01-01.

<hr>
<a name="address"/>

### 住所文字列
(Địa chỉ)

|Tên param|Database tương ứng|Loại data|Ý nghĩa|Ghi chú|
|-------|----------|-------|----------|----------|
|`j_jusho`|mast.jusho1, mast.jusho2, mast.jusho3|string|Search theo partial match|

<hr>
<a name="ken"/>

### 都道府県
(Tỉnh, thành phố)

|Tên param|Database tương ứng|Loại data|Ý nghĩa|
|-------|----------|-------|----------|
|`j_ken_option`||int||
|`j_bad_jusho`|mast.badjusho|array(2)|「住所無効以外」hoặc「住所無効のみ」|
|`j_ken`|mast.ken|array(48)|Tỉnh sinh sống|Khi không chọn select box thì không search bằng`j_ken`|

<hr>
<a name="chiku"/>

### 地区

|Tên param|Database tương ứng|Loại data|Ý nghĩa|
|-------|----------|-------|----------|
|`j_chiku_option`||int||
|`j_chiku`||array(14)|Chiku đang sinh sống|

<hr>
<a name="koko"/>

### 高校
(Trường cấp 3)

|Tên param|Database tương ứng|Loại data|Ý nghĩa|
|-------|----------|-------|----------|
|`j_koko`||string|`j_koko_option`:<br> - 名前（含む検索）: Search theo partial match field fullname của table uadmin.Koko<br> - コード（前方一致）: Search theo prefix match field kokocd của table Mast|
|`j_koko_option`||array(1)|「名前（含む検索）」hoặc「コード（前方一致）」|
|`j_koko_nozoku`||array(1)|「該当を除く」（có hoặc không）. Nếu có thì trả ra những record không thỏa mãn điều kiện search|

<hr>
<a name="yobiko"/>

### 予備校

|Tên param|Database tương ứng|Loại data|Ý nghĩa|
|-------|----------|-------|----------|
|`j_yobiko`||string|`j_yobiko_option`:<br> - 名前（含む検索）:Search theo partial match field fullname của table uadmin.Yobiko.<br> - コード（前方一致）: Search theo prefix match field yobikocd của table Mast|
|`j_yobiko_option`||array(1)|「名前（含む検索）」hoặc「コード（前方一致）」|
|`j_yobiko_nozoku`||array(1)|「該当を除く」（có hoặc không）. Nếu có thì trả ra những record không thỏa mãn điều kiện search|

<hr>
<a name="mail"/>

### メール

|Tên param|Database tương ứng|Loại data|Ý nghĩa|
|-------|----------|-------|----------|
|`j_mail1`|Sau khi join với `j_mail2` sẽ search bằng `mast.email`|string||
|`j_mail2`|Sau khi join với `j_mail1` sẽ search bằng `mast.email`|string||

<hr>
<a name="mail_option"/>

### メール有無

|Tên param|Database tương ứng|Loại data|Ý nghĩa|
|-------|----------|-------|----------|
|`j_addr_option`||int||
|`j_addr`||array(6)||

#### j_addr_option
|Giá trị|Biến Constant|Ý nghĩa|
|----|----|----|
|1|OPTION_IZUREKA|Lấy ra những item thõa mãn `một trong những` điều kiện|
|2|OPTION_IZUREKA_NOZOKU|Lấy những kết quả còn lại không phải là OPTION_IZUREKA|
|3|OPTION_SUBETE|Lấy ra những item thõa mãn `tất cả` điều kiện|
|4|OPTION_SUBETE_NOZOKU|Lấy những kết quả còn lại không phải là OPTION_SUBETE|

#### j_addr
|Giá trị|Biến Constant|Ý nghĩa|
|----|----|----|
|1|アドレス1に登録がある（有効）|`mast.email is not null` and `mast.email != ''` and `mast.bad_email = 0`|
|2|アドレス1に登録がある（無効）|`mast.email is not null` and `mast.email != ''` and `mast.bad_email = 1`|
|3|アドレス1に登録がない|`mast.email is null` or `mast.email = ''`|
|4|アドレス2に登録がある（有効）|`mast.kmail is not null` and `mast.kmail != ''` and `mast.bad_kmail = 0`|
|5|アドレス2に登録がある（無効）|`mast.kmail is not null` and `mast.kmail != ''` and `mast.bad_kmail = 1`|
|6|アドレス2に登録がない|`mast.kmail is null` or `mast.kmail = ''`|

<hr>
<a name="birth"/>

### 誕生日
(ngày sinh)

|Tên param|Database tương ứng|Loại data|Ý nghĩa|
|-------|----------|-------|----------|
|`j_birth_m_f`|Search `mast.birth` theo tháng của 誕生日|int|Từ tháng 〜月|
|`j_birth_d_f`|Search `mast.birth` theo ngày của 誕生日|int|Từ ngày 〜日|
|`j_birth_m_t`|Search `mast.birth` theo tháng của 誕生日|int|Đến tháng 〜月|
|`j_birth_d_t`|Search `mast.birth` theo ngày của 誕生日|int|Đến ngày 〜日|

**　Không quan tâm đến năm<br>
**　日付から、日付まで条件は〜日、〜月が2つなければ条件は無効になります。<br>
**　Nếu điều kiện search không có ngày và tháng thì sẽ vô hiệu。<br>
Ví dụ：Có giá trị `j_birth_m_f` mà không có giá trị `j_birth_d_f` thì điều kiện search sẽ không hữu hiệu。


<hr>
<a name="example"/>

### [志望](検索_志望)

## 流れ

```php
        $ids = [100001, 100002];
        $jokens = [
            'j_ids' => $ids,
        ];
        $joken = new Joken();
        $joken->setJokenParams($jokens);
        $kojin = new Kojin($joken);
        $kojin->setJokenArray($jokens);
        $mast_ids = $kojin->getMastIds();
```
