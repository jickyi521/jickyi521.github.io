---
layout: post
title: "iOS-tableview-reuse-cell"
date: 2014-06-17 09:45:31 +0800
comments: true
categories: iOS
---

第一次需要实例化一屏所能展 Contentview N个的实例入queue，对下次屏幕展示的view分别都重用这N个。

static NSString *identifier = @"cell";
UICustomerCell *cell = [tableView dequeueReusableCellWithIdentifier:identifier];

在 UICustomerCell 需要托人 UITableVIewCell 的控件 设置 identifier 为 "cell"

这样重用有重用，否则只是拖入的 UIView， 重用机制失效，每次还都会创建新的实例cell



Android里的重用 viewHolder

 @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        ViewHolder viewHolder = null;
        if (convertView == null) {
            convertView = View.inflate(mContext, R.layout.test, null);
            viewHolder = new ViewHolder();
            viewHolder.imageView = (ImageView) convertView.findViewById(R.id.item_image);
            viewHolder.titleTextView = (TextView) convertView.findViewById(R.id.item_text);
            convertView.setTag(viewHolder);
        } else {
            viewHolder = (ViewHolder) convertView.getTag();
        }
        return convertView;
    }


    class ViewHolder {
        ImageView imageView;
        TextView titleTextView;
    }