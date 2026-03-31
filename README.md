# Minimalistic-ERC721A
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract ERC721ABatch {
    string public name = "BatchNFT";
    string public symbol = "BNFT";

    mapping(uint256 => address) public ownerOf;
    mapping(address => uint256) public balanceOf;
    uint256 public totalSupply;
    uint256 public maxSupply = 5000;

    function batchMint(address to, uint256 quantity) public {
        require(totalSupply + quantity <= maxSupply, "Exceeds max supply");
        for (uint256 i = 0; i < quantity; i++) {
            uint256 tokenId = totalSupply + i + 1;
            ownerOf[tokenId] = to;
        }
        balanceOf[to] += quantity;
        totalSupply += quantity;
    }
}
