# view-product-buton-in-admin-page
Simple view product buton in admin page for OpenCart 2.0

View demo image - http://radidesign.net/wp-content/uploads/2015/12/view-button.jpg

Code in /admin/controller/catalog/product.php :
AFTER: 
'edit'       => $this->url->link('catalog/product/edit', 'token=' . $this->session->data['token'] . '&product_id=' . $result['product_id'] . $url, 'SSL')

ADD this code: 
$url = new Url(HTTP_CATALOG, $this->config->get('config_secure') ? HTTP_CATALOG : HTTPS_CATALOG),
'href'        => $url->link('product/product', 'path=' . $this->request->get['path'] . '&product_id=' . $result['product_id'] . $url)

and in /admin/view/template/catalog/product_list.tpl:
AFTER:
<td class="text-right"><a href="<?php echo $product['edit']; ?>" data-toggle="tooltip" title="<?php echo $button_edit; ?>" class="btn btn-primary"><i class="fa fa-pencil"></i></a>

ADD this code:

<a href="<?php echo $product['href']; ?>" data-toggle="tooltip" title="View product" class="btn btn-primary" target="_blank" ><i class="fa fa-eye"></i>

AND WORK
