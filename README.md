# nymey-trailer
nymey首页预告片下载

```
 
#!/bin/bash 


# 发起HTTP请求并获取HTML
html=$(curl -s "https://nymey.com/geo-restriction/")

# 从HTML中提取access_token
access_token=$(echo "$html" | grep -oP "localStorage.setItem\('access_token', \"\K[^\"]+")

# 打印提取到的access token


curl_dtr=$(curl -s --location 'https://apigateway.muvi.com/content' \
  -H 'authority: apigateway.muvi.com' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: zh-CN,zh;q=0.9' \
  -H "authorization: Bearer $access_token" \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -H 'origin: https://nymey.com' \
  -H 'pragma: no-cache' \
  -H 'referer: https://nymey.com/' \
  -H 'sec-ch-ua: "Not-A.Brand";v="99", "Chromium";v="124"' \
  -H 'sec-ch-ua-mobile: ?1' \
  -H 'sec-ch-ua-platform: "Android"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: cross-site' \
  -H 'user-agent: Mozilla/5.0 (Linux; Android 10; K) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/124.0.0.0 Mobile Safari/537.36' \
  --data-raw '{"query":"{featuredContentList(user_type:\":user_type\",end_user_uuid: \":me\",ip_address:\":ip\",app_token: \":app_token\", product_key: \":product_key\", store_key:\":store_key\", user_uuid:\":me\", feature_section_uuid:\"\",page_content:1,per_page_content:12,content_asset_type:\"\", maturity_rating_uuid: \":maturity_rating_uuid\", profile_uuid:\":profile_uuid\"){featured_content_list {feature_section_type feature_section_name feature_section_uuid  section_content_list {page_info{total_count} content_list{document_details{document_uuid file_url original_file_name file_name} maturity_rating content_created_by user_type  is_encoded is_playlist is_parent app_token product_key content_name is_free_content content_permalink content_search_tag content_trailer_uuid content_uuid content_parent_uuid content_desc content_asset_type content_asset_uuid no_image_available_url content_level categories{ category_name } trailer_details {video_uuid file_name file_url} video_details {is_feed  encoding_status encoding_end_time file_name  third_party_url } audio_details {audio_uuid encoding_status file_name  } posters {website{file_uuid file_url file_name} tv_apps{file_uuid file_url file_name} mobile_apps{file_uuid file_url file_name} } banners {website{file_uuid file_url file_name} tv_apps{file_uuid file_url file_name} mobile_apps{file_uuid file_url file_name}} }}}}}"}' \
  --compressed)

# 打印预告片file_urls
echo "$curl_dtr" | jq -r '.data.featuredContentList.featured_content_list[].section_content_list.content_list[] | select(.trailer_details != null) | .trailer_details.file_url'

```

```
~ $ bash nymey/nymey.sh







https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/526178802118487498128dc12d5d90f5/202407_________CharacterPV_89s_EN-1737820847757.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/6efef26c37a344cdb8a4e226ec1b7bd7/202501_S_______PV1_93s_EN-1736768153598.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/6efef26c37a344cdb8a4e226ec1b7bd7/202501_S_______PV1_93s_EN-1736768153598.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/6ff67fe90c2c495f8726d297a8e1c11b/MT2nd_teaser_h264_t2-1736505875057.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/a0ed718d7bd7433d8a065750af63b7da/fuguuPV2_128s_EN_re-1737028764003.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/89c9b08883e147f5a866be43e5398ccc/202407_______________PV1_90s_EN-1731901264813.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/526178802118487498128dc12d5d90f5/202407_________CharacterPV_89s_EN-1737820847757.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/6efef26c37a344cdb8a4e226ec1b7bd7/202501_S_______PV1_93s_EN-1736768153598.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/6efef26c37a344cdb8a4e226ec1b7bd7/202501_S_______PV1_93s_EN-1736768153598.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/6ff67fe90c2c495f8726d297a8e1c11b/MT2nd_teaser_h264_t2-1736505875057.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/a0ed718d7bd7433d8a065750af63b7da/fuguuPV2_128s_EN_re-1737028764003.mp4
https://d10xsoss226fg9.cloudfront.net/cN6YB0fU2ColhHGAv5NIjVGtN61G6zsU/3D28C83C85544F0D9517DD2E7C7EEDAA/vl/89c9b08883e147f5a866be43e5398ccc/202407_______________PV1_90s_EN-1731901264813.mp4
nymey/nymey.sh: line 36: unexpected EOF while looking for matching `''
```
