[S3の保存](https://docs.aws.amazon.com/sdk-for-ruby/v3/api/Aws/S3/Object.html#)

```rb
object.put({
  acl: "private", # accepts private, public-read, public-read-write, authenticated-read, aws-exec-read, bucket-owner-read, bucket-owner-full-control
  body: source_file,
  cache_control: "CacheControl",
  content_disposition: "ContentDisposition",
  content_encoding: "ContentEncoding",
  content_language: "ContentLanguage",
  content_length: 1,
  content_md5: "ContentMD5",
  content_type: "ContentType",
  checksum_algorithm: "CRC32", # accepts CRC32, CRC32C, SHA1, SHA256
  checksum_crc32: "ChecksumCRC32",
  checksum_crc32c: "ChecksumCRC32C",
  checksum_sha1: "ChecksumSHA1",
  checksum_sha256: "ChecksumSHA256",
  expires: Time.now,
  grant_full_control: "GrantFullControl",
  grant_read: "GrantRead",
  grant_read_acp: "GrantReadACP",
  grant_write_acp: "GrantWriteACP",
  metadata: {
    "MetadataKey" => "MetadataValue",
  },
  server_side_encryption: "AES256", # accepts AES256, aws:kms
  storage_class: "STANDARD", # accepts STANDARD, REDUCED_REDUNDANCY, STANDARD_IA, ONEZONE_IA, INTELLIGENT_TIERING, GLACIER, DEEP_ARCHIVE, OUTPOSTS, GLACIER_IR
  website_redirect_location: "WebsiteRedirectLocation",
  sse_customer_algorithm: "SSECustomerAlgorithm",
  sse_customer_key: "SSECustomerKey",
  sse_customer_key_md5: "SSECustomerKeyMD5",
  ssekms_key_id: "SSEKMSKeyId",
  ssekms_encryption_context: "SSEKMSEncryptionContext",
  bucket_key_enabled: false,
  request_payer: "requester", # accepts requester
  tagging: "TaggingHeader",
  object_lock_mode: "GOVERNANCE", # accepts GOVERNANCE, COMPLIANCE
  object_lock_retain_until_date: Time.now,
  object_lock_legal_hold_status: "ON", # accepts ON, OFF
  expected_bucket_owner: "AccountId",
})
```

